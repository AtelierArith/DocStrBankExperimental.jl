```
latexarray{T}(arr::AbstractArray{T, 2})
```

[`latexraw`](@ref)を使用してLaTeX配列環境を作成します。

# 例

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
