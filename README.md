# Computer vision 
### Edge detection
[![Architecture diagram of yassakamille/computer_vision-edge_detection](https://gitdiagram.com/yassakamille/computer_vision-edge_detection/diagram.png)](https://gitdiagram.com/yassakamille/computer_vision-edge_detection?utm_source=readme&utm_medium=picture)

## Harris Corner Detection Workflow
## Harris Corner Detection Workflow

```mermaid
flowchart TD
    subgraph custom["Custom Harris Corner Detector"]
        runner["Image-Pair Demo<br/>Code.py"]
        gradients["Sobel Gradients"]
        smoothing["Gaussian Smoothing"]
        response["Harris Response Calculation"]
        scaling["Response Rescaling"]
        suppression["Non-Maximum Suppression"]
        threshold["Response Thresholding"]
    end

    subgraph utilities["Gradient Utilities"]
        sobel["get_gradients_xy()<br/>Utilities.py"]
        rescale["rescale()<br/>Utilities.py"]
    end

    subgraph opencv["OpenCV Reference Implementation"]
        reference["OpenCV Harris Demo<br/>get_harris.py"]
        dilation["Corner Response Dilation"]
        marking["Corner Marking and Display"]
    end

    images["Sample Image Pairs<br/>check.bmp / check_rot.bmp"]
    results["Custom Detection Results"]
    reference_image["OpenCV Detection Result"]

    images --> runner
    runner --> gradients
    gradients --> sobel
    sobel --> smoothing
    smoothing --> response
    response --> scaling
    scaling --> rescale
    rescale --> suppression
    suppression --> threshold
    threshold --> results

    reference --> dilation
    dilation --> marking
    marking --> reference_image

    click runner "https://github.com/yassakamille/computer_vision-edge_detection/blob/main/Harris/Code.py"
    click sobel "https://github.com/yassakamille/computer_vision-edge_detection/blob/main/Harris/Utilities.py"
    click rescale "https://github.com/yassakamille/computer_vision-edge_detection/blob/main/Harris/Utilities.py"
    click reference "https://github.com/yassakamille/computer_vision-edge_detection/blob/main/Harris/get_harris.py"
    click images "https://github.com/yassakamille/computer_vision-edge_detection/tree/main/Harris/input"

    classDef process fill:#dbeafe,stroke:#2563eb,stroke-width:1.5px,color:#172554
    classDef utility fill:#fef3c7,stroke:#d97706,stroke-width:1.5px,color:#78350f
    classDef result fill:#dcfce7,stroke:#16a34a,stroke-width:1.5px,color:#14532d
    classDef inputStyle fill:#e0e7ff,stroke:#4f46e5,stroke-width:1.5px,color:#312e81

    class runner,gradients,smoothing,response,suppression,threshold,reference,dilation,marking process
    class sobel,rescale,scaling utility
    class results,reference_image result
    class images inputStyle
```
[![Architecture diagram](https://gitdiagram.com/diagram-badge.svg)](https://gitdiagram.com/yassakamille/computer_vision-edge_detection?utm_source=readme&utm_medium=badge)
