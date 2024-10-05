# Python-Data-Science-ML-Reference-Sheet

name: Compile LaTeX Document

on:
  push:
    branches:
      - main  # Change to your default branch if different

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Set up LaTeX environment
      run: sudo apt-get update && sudo apt-get install -y texlive-full
    - name: Compile LaTeX
      run: |
        pdflatex -interaction=nonstopmode main.tex
    - name: Upload PDF as artifact
      uses: actions/upload-artifact@v2
      with:
        name: compiled-pdf
        path: refsheet.pdf
