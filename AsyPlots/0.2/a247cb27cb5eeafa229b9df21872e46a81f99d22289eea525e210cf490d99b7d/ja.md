```
animate(filename::AbstractString,
        plots::Vector{Plot2D};
        rate=10)

animate(plots::Vector{Plot2D};rate=10)
```

`plots` から `.mp4` ビデオを作成し、フレームレートは `rate` です。

"filename" が指定されている場合、ムービーファイルはそこに保存されます。そうでない場合、ムービーは開かれます。

# 例

```julia
X = cumsum(randn(100000))
Y = cumsum(randn(100000))
plots = [Plot(Path(X[1:t],Y[1:t])) for t=10:10:10000]
animate(plots)
```
