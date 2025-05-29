Provides unofficial implementations (in the form of `ODESystem` and `ODEFunction` instances) of a polynomial approximation for longitudinal aircraft dynamics. Specifically, these models approximate NASA's Generic Transport Model – a radio-controlled, sub-scale model aircraft which is used flight control research. These publicly available equations were published by [Chakraborty et al](https://www.sciencedirect.com/science/article/abs/pii/S0967066110002595).

# Extended help

## License

MIT License

Copyright (c) 2021 Joe Carpinelli

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Exports

  * [`GTM`](@ref)
  * [`GTMFunction`](@ref)

## Imports

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `LinearAlgebra`
  * `Memoize`
  * `ModelingToolkit`
  * `Symbolics`
