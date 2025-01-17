# Florence-2 RESTful API

This project implements a web service that exposes Microsoft's Florence-2 model via a RESTful API. The service allows users to interact with the model for various tasks such as object detection, image segmentation, image captioning and text extraction.

## Features
- **Image Classification**: Classify the main object in an image.
- **Object Detection**: Detect and localize objects in an image (returns bounding boxes and confidence scores).
- **Task Management**: List available tasks such as classification and detection.

## Requirements

### Server-side:
- Python 3.9 or later
- FastAPI
- Uvicorn (for running the FastAPI server)
- HuggingFace Transformers (for loading the Florence-2 model)
- Pillow (for image processing)
- Supervision (for object detection post-processing)

### Client-side:
- Requests (for making HTTP requests)
- Supervision (for handling object detection results)


## Setup

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
    ```

2. Install the requirements
    ```bash
   pip install -r requirements.txt
    ```

## Running the Server

3. Run the FastAPI server
    ```bash
   uvicorn main:app --reload
    ```
    The server will run on http://localhost:8000

4. API Endpoints
   GET /tasks will return all the supported tasks
    ```bash
   curl http://localhost:8000/tasks
    ```

   POST /predict Takes as arguments the file path of the image, teh supported ```task_type``` and the optional ```text_input``` for the supported tasks
    ```bash
   curl -X POST "http://localhost:8000/predict" -F "file=@<image_path>" -F "task_type=<task_type>" -F "text_input=<text_input>"
    ```

5. Test the API by running the client
    ```bash
   python client.py
    ```
