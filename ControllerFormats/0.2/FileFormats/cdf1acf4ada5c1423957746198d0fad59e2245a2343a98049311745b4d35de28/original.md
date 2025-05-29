```
read_POLAR(filename::String)
```

Read a neural network stored in POLAR format.

### Input

  * `filename` – name of the POLAR file

### Output

A [`FeedforwardNetwork`](@ref).

### Notes

The POLAR format uses the same parameter format as Sherlock (see [`read_Sherlock`](@ref)) but allows for general activation functions.

In addition, the last two lines are:

```
0.0
1.0
```

The reference parser and writer can be found [here](https://github.com/ChaoHuang2018/POLAR_Tool/blob/8df333a59321f45227dafc87c367779783b6166c/POLAR/neuralnetwork.py).
