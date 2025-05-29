Data = ExampleData(SigName::String)

Imports sample data time series with specific properties that are commonly  used as benchmarks for assessing the performance of various entropy methods. The datasets returned by ExampleData() are used in the examples provided in documentation on www.EntropyHub.xyz and elsewhere. ***Note*** ExampleData() requires an internet connection to download and import the required datasets!

`Data`is the sample dataset imported corresponding to the string input `SigName` which can be one of the following string:

# Arguments:

`SigName`   -  

```
        `uniform`          - uniformly distributed random number sequence in range [0 1], N = 5000
        `randintegers`     - randomly distributed integer sequence in range [1 8], N = 4096
        `gaussian`         - normally distributed number sequence [mean: 0, SD: 1], N = 5000
        `henon`            - X and Y components of the Henon attractor [alpha: 1.4, beta: .3, Xo = 0, Yo = 0], N = 4500
        `lorenz`           - X, Y, and Z components of the Lorenz attractor [sigma: 10, beta: 8/3, rho: 28, Xo = 10, Yo = 20, Zo = 10], N = 5917
        `chirp`            - chirp signal (f0 = .01, t1 = 4000, f1 = .025), N = 5000
        `uniform2`         - two uniformly distributed random number sequences in range [0,1], N = 4096
        `gaussian2`        - two normally distributed number sequences [mean: 0, SD: 1], N = 3000
        `randintegers2`    - two uniformly distributed pseudorandom integer sequences in range [1 8], N = 3000
        `uniform_Mat`      - matrix of uniformly distributed random numbers in range [0 1], N = 50 x 50
        `gaussian_Mat`     - matrix of normally distributed numbers [mean: 0, SD: 1], N = 60 x 120
        `randintegers_Mat` - matrix of randomly distributed integers in range [1 8], N = 88 x 88
        `mandelbrot_Mat`   - matrix representing a Mandelbrot fractal image with values in range [0 255], N = 92 x 115
        `entropyhub_Mat`   - matrix representing the EntropyHub logo with values in range [0 255], N = 127 x 95
                     
For further info on these graining procedures see the `EntropyHub guide <https://github.com/MattWillFlood/EntropyHub/blob/main/EntropyHub%20Guide.pdf>`_.
```
