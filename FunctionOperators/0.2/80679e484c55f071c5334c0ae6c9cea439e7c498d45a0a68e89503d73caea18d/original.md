**Recycling macro**: Reduce the number of allocations inside a for loop by preallocation of arrays for the outputs of marked operations. Markers: `@♻` (`\:recycle:`), `🔝` (`\:top:`), `🔃` (`\:arrows_clockwise:`), and `@🔃`

Macro @♻ should be placed right before a for loop, and then it executes the following substitutions:

  * **Expressions marked by `🔝`:**

They are going to be calculated before the loop, the result is stored in a variable, and the expression will be replaced by that variable. It also can be useful when a constant expression is used in the loop, but the idea behind creating that substitution is to allow caching of composite FunctionMatrices. Eg:

```julia
@♻ for i=1:5
    result = 🔝((FuncOp₁ + 2I) * FuncOp₂) * data
end
```

will be transformed to 

```julia
🔝_1 = (FuncOp₁ + 2I) * FuncOp₂
for i = 1:5
    result = 🔝_1 * data
end
```

so that way plan is calculated only once, and also buffers for intermediate results of the composite operator are allocated once.

  * **Expressions marked by `🔃`:**

They are going to be calculated before the loop (to allocate an array to store the result), but the expression is also evaluated in each loop iteration. The difference after the substitution is that the result of the expression is always saved to the preallocated array. Eg:

```julia
@♻ for i=1:5
    result = FuncOp₁ * 🔃(A + B)
end
```

will be transformed to 

```julia
🔃_1 = A + B
for i = 1:5
    result = FuncOp₁ * @.(🔃_1 = A + B)
end
```

This transformation first allocates an array named `🔃_1`, and then in every iteration it is recalculated, saved to `🔃_1`, and the this value is used for the rest of the operation (i.e.: `FuncOp₁ * 🔃_1`. Note that `@.` macro is inserted before the inline assignment. This is needed otherwise `A + B` would allocate a new array before it is stored in `🔃_1`. **Warning!** It can break your code, e.g. `@.(🔃_1 = A * B) ≠ (🔃_1 = A .* B)` {matrix multiplication vs. elementwise multiplication}! On the other hand, when the marked expression consists only a multiplication, then it is transformed into a call of `mul!`. Eg:

```julia
@♻ for i=1:5
    result = FuncOp₁ * 🔃(A * B)
end
```

will be transformed to 

```julia
🔃_1 = A * B
for i = 1:5
    result = FuncOp₁ * mul!(🔃_1, A, B)
end
```

  * **Lastly, assignments marked by `@🔃`:**

They will be transformed into a call of `mul!`. Of course, it works only if `@🔃` is directly followed by an assignment that has a single multiplication on the right side. Eg:

```julia
@♻ for i=1:5
    @🔃 result = FuncOp₁ * A
end
```

will be transformed to 

```julia
result = FuncOp₁ * A
for i = 1:5
    mul!(result, FuncOp₁, A)
end
```

Final note: `🔝` can be arbitrarily nested, and it can be embedded in expressions marked by `🔃`. `🔃` can also be nested, and it can be used in assigments marked by `@🔃` (along with `🔝`, of course).
