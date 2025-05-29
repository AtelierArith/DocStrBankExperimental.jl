```
vectorize(tc::MicroTC, text; bow=BOW(), textconfig=tc.textconfig, normalize=true)
vectorize(tc::MicroTC, bow::BOW; normalize=true)
```

Creates a weighted vector using the model. The input `text` can be a string or an array of strings; it also can be an already computed bag of words.
