```
targets([f], data, [obsdim])
```

`data` から具体的なターゲットを抽出し、それらを返します。

この関数は、`data` の型に対して [`gettargets`](@ref) のカスタムメソッドが実装されていない限り、常に [`getobs`](@ref) を呼び出すという意味でイーガーです。これにより、`DataSubset` や `SubArray` のようなプレースホルダーではなく、実際の値が返されることが保証されます。

```julia
julia> targets(DataSubset([1,2,3]))
3-element Array{Int64,1}:
 1
 2
 3
```

`data` がタプルの場合、慣例としてタプルの最後の要素にターゲットが含まれ、関数は一度（そして一度だけ）再帰されます。

```julia
julia> targets(([1,2], [3,4]))
2-element Array{Int64,1}:
 3
 4

julia> targets(([1,2], ([3,4], [5,6])))
([3,4],[5,6])
```

`f` が提供されると、[`gettarget`](@ref) が `data` の各観測に適用され、結果がベクトルとして返されます。

```julia
julia> targets(argmax, [1 0 1; 0 1 0])
3-element Array{Int64,1}:
 1
 2
 1
```

オプションのパラメータ `obsdim` は、`data` の型に対して観測を示す次元を指定するために使用できます。この概念が意味を持つ場合に限ります。詳細については `?ObsDim` を参照してください。

```julia
julia> targets(argmax, [1 0; 0 1; 1 0], obsdim=1)
3-element Array{Int64,1}:
 1
 2
 1
```
