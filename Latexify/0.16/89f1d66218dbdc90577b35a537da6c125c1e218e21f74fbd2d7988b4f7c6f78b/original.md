```
latexarray{T}(arr::AbstractArray{T, 2})
```

Create a LaTeX array environment using [`latexraw`](@ref).

# Examples

```julia
arr = [1 2; 3 4]
latexarray(arr)
```

$$
"\begin{equation}
\left[
\begin{array}{cc}
1 & 2\\ 
3 & 4\\ 
\end{array}
\right]
\end{equation}
"
$$
