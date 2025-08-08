# SQL Query Generator using Fine-tuned Llama-2

This project fine-tunes the Llama-2-7B model on a specialized SQL dataset to create an intelligent SQL query generator. The model can understand natural language instructions about database operations and generate corresponding SQL queries with proper syntax and logic.

## Key Features

- **Efficient Fine-tuning**: Uses LoRA and 4-bit quantization to reduce memory requirements
- **SQL Code Generation**: Converts natural language to SQL queries
- **Production-Ready**: Optimized for deployment with quantization techniques
- **Educational**: Demonstrates modern LLM training techniques

## 🛠️ Technologies Used

- **Model**: Meta's Llama-2-7B-hf
- **Fine-tuning**: LoRA (Low-Rank Adaptation) with PEFT
- **Quantization**: 4-bit quantization with BitsAndBytes
- **Framework**: PyTorch, Transformers, TRL
- **Dataset**: ChrisHayduk/Llama-2-SQL-Dataset
- **Platform**: Google Colab (TPU/GPU compatible)

## 📊 Dataset Information

- **Source**: ChrisHayduk/Llama-2-SQL-Dataset
- **Training Samples**: 1,000 (subset for efficient training)
- **Total Dataset**: 70,719 instruction-following examples
- **Format**: Natural language instruction → SQL query pairs

## 📊 Technical Architecture
Input: Natural Language Question
↓
Llama-2-7B Base Model
↓
LoRA Adapters (Fine-tuned)
↓
4-bit Quantized Inference
↓
Output: SQL Query

## Model Specifications

- **Base Model**: NousResearch/Llama-2-7b-hf
- **LoRA Rank**: 16
- **LoRA Alpha**: 32
- **Target Modules**: All attention and MLP layers
- **Quantization**: 4-bit NF4 with float16 compute
- **Training Data**: 1,000 samples (subset for efficient training)

## Training Configuration

- **Learning Rate**: 2e-4
- **Batch Size**: 1 (with gradient accumulation of 4)
- **Epochs**: 1
- **Optimizer**: Paged AdamW 8-bit
- **Scheduler**: Cosine with 5% warmup

## Efficiency Metrics

- **Trainable Parameters**: ~40M (0.59% of total model)
- **Memory Usage**: Significantly reduced through 4-bit quantization
- **Training Time**: ~1 hour on Google Colab TPU

## 📁 Project Structure
sql-query-generator/
├── SQL_Query_Generator.ipynb    # Main training notebook
├── README.md                    # Project documentation
├── requirements.txt             # Dependencies
└── fine_tuned_llama_sql/       # Saved model (after training)
├── adapter_config.json
├── adapter_model.safetensors
└── tokenizer files

## 🎯 Use Cases

- **Database Query Assistance**: Help non-technical users write SQL
- **Educational Tool**: Learn SQL through natural language examples
- **Development Productivity**: Rapid SQL prototyping
- **Data Analysis**: Quick query generation for BI

## 🔬 Key Technical Achievements

- **Parameter Efficient Fine-tuning**: Using LoRA for efficient adaptation
- **Model Quantization**: 4-bit quantization for memory optimization
- **Code Generation**: Training LLMs for structured SQL output
- **Resource Optimization**: Large model training on limited hardware
