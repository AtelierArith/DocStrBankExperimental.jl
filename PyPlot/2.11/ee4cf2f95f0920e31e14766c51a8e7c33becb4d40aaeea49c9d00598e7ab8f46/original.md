PyPlot allows Julia to interface with the Matplotlib library in Python, specifically the matplotlib.pyplot module, so you can create beautiful plots in Julia with your favorite Python package.

Only the currently documented matplotlib.pyplot API is exported. To use other functions in the module, you can also call matplotlib.pyplot.foo(...) as plt.foo(...). For example, plt.plot(x, y) also works. (And the raw PyObject for the matplotlib modules is also accessible as PyPlot.matplotlib.)

In general, all the arguments are the same as in Python.

Here's a brief demo of a simple plot in Julia:

```
using PyPlot
x = range(0; stop=2*pi, length=1000); y = sin.(3 * x + 4 * cos.(2 * x));
plot(x, y, color="red", linewidth=2.0, linestyle="--")
title("A sinusoidally modulated sinusoid")
```

For more information on API, see the matplotlib.pyplot documentation and the PyPlot GitHub page.
