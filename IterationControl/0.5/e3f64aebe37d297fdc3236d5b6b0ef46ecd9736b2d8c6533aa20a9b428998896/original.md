```
Data(my_data; stop_when_exhausted=false)
```

An iteration control, as in, `Data(rand(100))`. 

In each application of this control a new `item` from the iterable, `data`, is retrieved (using `iterate`) and `IterationControl.ingest!(m, item)` is called. Here `m` is the object being iterated. 

A control becomes passive once the `data` iterable is done. To trigger a stop *after one passive application of the control*, set `stop_when_exhausted=true`. 
