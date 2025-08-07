# LangGraph BMI Calculator

A Body Mass Index (BMI) calculator built using LangGraph's state management system. This project demonstrates how to create a sequential workflow for health calculations with type-safe state management.

## 🎯 Overview

This application calculates BMI from weight and height inputs and automatically categorizes the result according to World Health Organization (WHO) standards. The implementation showcases LangGraph's capabilities for building structured, sequential workflows.

## ✨ Features

- **Type-Safe State Management**: Uses TypedDict for structured data handling
- **Sequential Workflow Processing**: Implements a clear calculation → classification pipeline
- **WHO Standard Classifications**: Accurate BMI categorization based on international standards
- **Interactive Jupyter Notebook**: Well-documented code with explanations and examples
- **Modular Design**: Separate functions for calculation and classification logic

## 🏗️ Architecture

The BMI calculator is implemented as a LangGraph workflow with two main processing nodes:

```
START → Calculate BMI → Classify BMI → END
```

### State Structure
```python
class bmistate(TypedDict):
    weight: float    # Weight in kilograms
    height: float    # Height in meters
    bmi: float       # Calculated BMI value
    category: str    # BMI classification category
```

### Processing Steps
1. **BMI Calculation**: Computes BMI using the formula `weight (kg) / height² (m²)`
2. **BMI Classification**: Categorizes the result into standard WHO classifications

## 📊 BMI Classifications

| BMI Range | Category |
|-----------|----------|
| < 18.5 | Underweight |
| 18.5 - 24.9 | Normal weight |
| 25.0 - 29.9 | Overweight |
| ≥ 30.0 | Obesity |

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook or JupyterLab
- LangGraph library

### Installation

1. Clone the repository:
```bash
git clone https://github.com/wazzuwu/LangGraph-BMI.git
cd LangGraph-BMI
```

2. Create and activate a virtual environment:
```bash
python -m venv lenv
# On Windows
lenv\Scripts\activate
# On macOS/Linux
source lenv/bin/activate
```

3. Install required dependencies:
```bash
pip install langgraph jupyter
```

### Usage

1. Open the Jupyter notebook:
```bash
jupyter notebook test.ipynb
```

2. Run the cells sequentially to see the BMI calculator in action

3. Modify the input values in the last cell to test with different weight/height combinations:
```python
init_state = bmistate(weight=70, height=1.75, bmi=0.0)
result = workflow.invoke(init_state)
print(result)
```

## 📁 Project Structure

```
LangGraph-BMI/
├── test.ipynb          # Main Jupyter notebook with BMI calculator
├── README.md           # Project documentation
├── lenv/              # Virtual environment (created after setup)
└── requirements.txt   # Python dependencies (if created)
```

## 🧪 Example Usage

```python
# Initialize state with sample data
init_state = bmistate(weight=105, height=1.70, bmi=0.0)

# Execute the workflow
result = workflow.invoke(init_state)

# Output: {'weight': 105, 'height': 1.7, 'bmi': 36.3, 'category': 'Obesity'}
```

## 🔧 Technical Implementation

### Key Components

- **LangGraph StateGraph**: Manages the workflow execution
- **TypedDict State**: Ensures type safety and clear data structure
- **Sequential Processing**: Two-step calculation and classification pipeline
- **Error Handling**: Built-in validation through type hints

### Dependencies

- `langgraph`: State graph management and workflow orchestration
- `typing`: Type hints and TypedDict support

## 🚀 Possible Extensions

- **Input Validation**: Add range checks for weight and height values
- **Unit Conversion**: Support for imperial units (pounds/feet)
- **Additional Metrics**: Include body fat percentage, BMR calculations
- **Visualization**: Add charts for BMI categories and trends
- **API Integration**: Create a REST API wrapper
- **Database Storage**: Store calculation history and user profiles




## 🙋‍♂️ Author

**wazzuwu** - [GitHub Profile](https://github.com/wazzuwu)



*Built with ❤️ using LangGraph and Python*
