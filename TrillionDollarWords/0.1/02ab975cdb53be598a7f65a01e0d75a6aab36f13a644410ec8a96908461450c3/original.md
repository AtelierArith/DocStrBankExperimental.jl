```
load_model
```

Loads the model presented in the paper from HuggingFace. If `load_head` is `true`, the model is loaded with the head (i.e. the final layer) for classification. If `load_head` is `false`, the model is loaded without the head. The latter is useful for fine-tuning the model on a different task or in case the classification head is not needed. Accepts any additional keyword arguments that are accepted by `Transformers.HuggingFace.HGFConfig`.
