
# MachineLearningNotes

a collection of notebooks for learning machine learning.

## running on Colab

when running on Colab, we need to set up PlaidML on the GPU.

First, enable the GPU: go to `Runtime > Change runtime type` and select **GPU** as the accelerator

Then, add the following cell at the start of the notebook:

```py
# install PlaidML support for Keras
%pip install plaidml plaidml-keras plaidbench

# set keras backend to PlaidML
import os
os.environ["KERAS_BACKEND"] = "plaidml.keras.backend"

# setup PlaidML using device #2 (GPU)
!printf 'n\n2\ny' | plaidml-setup

# dump the PlaidML config
!printf "plaidml config:"
!cat ~/.plaidml

# run PlaidBench on a simple network to ensure everything works
!plaidbench keras mobilenet
```
