# Retrieval-Augmented Generation for Enterprise Knowledge 

## Project Overview
Organizations store large volumes of enterprise knowledge across multiple platforms such as SharePoint, emails, and internal QA systems. This information is often fragmented, unstructured, and difficult to search effectively, leading to inefficiencies in retrieving relevant insights.

Traditional keyword-based search tools struggle to understand context and intent, resulting in low relevance and lack of traceability. Additionally, enterprises require strict security, access control, and compliance when handling sensitive internal data.

To overcome these challenges, the organization is deploying a Retrieval-Augmented Generation (RAG) system.
### Objectives
* Centralize enterprise knowledge
  * to unify data sources from SharePoint, emails, and internal QA systems
* Semantic search with citation
  * to enable semantic understanding of the keyword search
* Decision-making efficiency
  * to provide accurate responses in shorter time spent
* Data governance
  * to ensure enterprise-grade security and access control using Azure-native services

## Architecture & Design Decisions
### Retrieval Augmented Generation (RAG) Fundemental
* RAG is a technique that combines the capabilities of a pre-trained large language model (LLM) with an external data source (Vector Database).

<p align="center">
    <img src="images/rag.png" alt="RAG" width="1200">
</p>   

### Document Search Process flow
<p align="center">
    <img src="images/rag_enterprise.png" alt="RAG Enterprise" width="1200">
</p>

* Data sources
    * SharePoint Doc, emails and QA records
* Ingestion & Processing
    * data is ingested from multiple enterprise platforms
    * Content is extracted, cleaned, and transformed into standardized formats for downstream processing
* Indexing & retrieval
    * data is indexing with the selected embedding model and stored in a vector database
    * retrieval combines:
        * semantic similarity (vector search)
        * lexical matching (rapidfuzz for character-based scoring) 
<p align="center">
    <img src="images/hybrid_search.png" alt="Hybrid Search" width="1000">
</p>

* RAG generation
    * Relevant document chunks are retrieved and provided as context to the language model (model='gpt-4.1-mini')
    * The model generates grounded responses based on retrieved content
    * Responses include citations to source documents for traceability
* User interface (UI)
    * Users can query the system via Chat & Search App using natural language prompts
    * The system returns relevant clickable citations

## Solution Review and Execution
## Dependencies
* pandas>=2.0.0
* numpy>=1.24.0
* databricks-vectorsearch>=2.19.0
* rapidfuzz
* openai

## Installation and execution
1. Clone the repository: git clone https://github.com/ongsm/cerecon.git

## Limitations
* Time constraints limited further model performance improvement.

