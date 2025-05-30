```julia
struct HomotopyNonlinearFunction{iip, specialize, F, P, Q, D} <: SciMLBase.AbstractNonlinearFunction{iip}
```

A representation of a polynomial nonlinear system of equations given by

$$
0 = f(polynomialize(u, p), p)
$$

Designed to be used for solving with HomotopyContinuation.

## Constructor

Note that only the function `f` is required. This function should be given as `f!(du,u,p)` or `du = f(u,p)`. See the section on `iip` for more details on in-place vs out-of-place handling.

To provide the Jacobian function etc, `f` must be a [`NonlinearFunction`](@ref) with the required fields populated.

## iip: In-Place vs Out-Of-Place

For more details on this argument, see the ODEFunction documentation.

## specialize: Controlling Compilation and Specialization

For more details on this argument, see the ODEFunction documentation.

## Fields

The fields of the `HomotopyNonlinearFunction` type directly match the names of the inputs.

  * `f`: The polynomial function `f`. Stored as a `NonlinearFunction{iip, specialize}`. If not provided to the constructor as a `NonlinearFunction`, it will be appropriately wrapped.

  * `polynomialize`: The nonlinear system may be a polynomial of non-polynomial functions. For example,

    $$
    sin^2(x^2) + 2sin(x^2) + 1 = 0
    log(x + y) ^ 3 = 0.5
    $$

    is a polynomial in `[sin(x^2), log(x + y)]`. To allow for such systems, `polynomialize` converts the state vector of the original system (termed as an "original space" vector) to the state vector of the polynomial system (termed as a "polynomial space" vector). In the above example, it will be the function:

    ```julia
    function polynomialize(u, p)
      x, y = u
      return [sin(x^2), log(x + y)]
    end
    ```

    We refer to `[x, y]` as being in "original space" and `[sin(x^2), log(x + y)]` as being in "polynomial space".

    This defaults to a function which returns `u` as-is.

  * `unpolynomialize`: The inverse operation of `polynomialize`.

    This function takes as input a vector `u′` in "polynomial space" and returns a collection of vectors `uᵢ ∀ i ∈ {1..n}` in "original space" such that `polynomialize(uᵢ, p) == u′ ∀ i`. A collection is returned since the mapping may not be bijective. For periodic functions which have infinite such vectors `uᵢ`, it is up to the user to choose which ones to return.

    In the aforementioned example in `polynomialize`, this function will be:

    ```julia
    function unpolynomialize(u, p)
      a, b = u
      return [
        [sqrt(asin(a)), exp(b) - sqrt(asin(a))],
        [-sqrt(asin(a)), exp(b) + sqrt(asin(a))],
      ]
    end
    ```

    There are of course an infinite number of such functions due to the presence of `sin`. This example chooses to return the roots in the interval `[-π/2, π/2]`.

  * `denominator`: A function of the form `denominator(u, p) -> denoms` where `denoms` is an array of denominator terms which cannot be zero. This is useful when `f` represents the numerator of a rational function. Roots of `f` which cause any of the values in `denoms` to be below a threshold will be excluded. Note that here `u` must be in "polynomial space".
