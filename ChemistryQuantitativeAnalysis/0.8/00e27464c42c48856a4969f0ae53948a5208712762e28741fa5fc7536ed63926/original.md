```
eachsample(dt::AbstractDataTable)
```

Create an iterator which gets data belonging to each sample as a `Vector`. For `SampleDataTable`, new vectors are created; mutating these vector will not change the value in `dt`.
