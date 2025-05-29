```
noise_model(sys::AbstractPredictionStateSpace)
```

Return a model of the noise driving the system, `v`, in

$$
x' = Ax + Bu + Kv\\
y = Cx + Du + v
$$

The model neglects u and is given by

$$
x' = Ax + Kv\\
y = Cx + v
$$

Also called the "innovation form". This function calls `ControlSystemsBase.innovation_form`.
