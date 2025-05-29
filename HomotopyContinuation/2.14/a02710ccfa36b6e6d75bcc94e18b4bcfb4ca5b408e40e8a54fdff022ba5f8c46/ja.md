```
write_solutions(filename, solutions)
```

ディスクにプレーンテキストファイルとして保存します。ストレージ形式は次のとおりです。最初の行は保存されたソリューションの数を示し、その後に空行が続きます。次に、各ソリューションが空行で区切られて保存されます。ソリューションは*常に*複素数として考慮されることに注意してください。ソリューションファイルを読み込むには、[`read_solutions`](@ref)を参照してください。

これは[Bertini](https://bertini.nd.edu)で使用されるのと同じファイル形式であることに注意してください。

## 例

```julia
julia> write_solutions("solutions.txt", [[1, 1], [-1, 2]])

shell> cat solutions.txt
2

1 0
1 0

-1 0
2 0

julia> read_solutions("solutions.txt")
2-element Array{Array{Complex{Int64},1},1}:
 [1 + 0im, 1 + 0im]
 [-1 + 0im, 2 + 0im]
```
