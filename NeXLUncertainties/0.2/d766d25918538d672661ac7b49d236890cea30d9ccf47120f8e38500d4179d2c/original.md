```
value(uvs::UncertainValues, lbl::Label)
value(uvs::UncertainValues, lbl::Label, defValue)
```

The value associate with the Label. The first implementation throws an exception if `lbl` is not present while the second implementation returns `defValue`
