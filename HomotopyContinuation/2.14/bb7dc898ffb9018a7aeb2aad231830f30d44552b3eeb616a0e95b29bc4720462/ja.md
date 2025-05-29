```
write_parameters(filename, parameters)
```

パラメータをプレーンテキストファイルとしてディスクに保存します。ストレージフォーマットは次のとおりです。最初の行は保存されたパラメータ値の数を示し、その後に空行が続きます。次に、パラメータ値が保存されます。

[`read_parameters`](@ref)を参照してください。

これは[Bertini](https://bertini.nd.edu)で使用されるのと同じファイルフォーマットであることに注意してください。

## 例

```julia
julia> write_parameters("parameters.txt", [2.0, -3.2 + 2im])

shell> cat parameters.txt
2

2.0 0.0
-3.2 2.0

julia> read_parameters("parameters.txt")
2-element Array{Complex{Float64},1}:
  2.0 + 0.0im
 -3.2 + 2.0im
```
