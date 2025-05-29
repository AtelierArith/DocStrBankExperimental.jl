```
eachobs(data, [obsdim])
```

`data`を1つの観測値ずつ反復処理します。`data`の型がサポートしている場合、メモリ効率のためにバッファが事前に割り当てられ再利用されます。

重要: `collect`の使用は避けてください。一般的に、各反復で同じオブジェクトが変更された値を返す可能性があります。そのような動作が望ましくない場合は、代わりに`obsview`を使用してください。

```julia
X = rand(4,100)
for x in eachobs(X)
    # ループは100回実行されます
    @assert typeof(x) <: Vector{Float64}
    @assert size(x) == (4,)
end
```

配列の場合、観測値は最後の配列次元で表されると仮定されます。これは上書き可能です。

```julia
# 今回は行列の次元を反転させます
X = rand(100,4)
A = eachobs(X, obsdim=1)
# 挙動は以前と同じです
@assert eltype(A) <: Array{Float64,1}
@assert length(A) == 100
```

複数の変数がサポートされています（例: ラベル付きデータの場合）

```julia
for (x,y) in eachobs((X,Y))
    # ...
end
```

内部的に`eachobs(data, obsdim)`は`BufferGetObs(obsview(data, obsdim))`にマッピングされることに注意してください。

```julia
@assert typeof(eachobs(X)) <: BufferGetObs
@assert typeof(eachobs(X).iter) <: ObsView
```

これは、次のコードがほぼ同等であることを意味します。

```julia
for obs in eachobs(data, obsdim)
    # ...
end
```

おおよそ次のように等価です。

```julia
obs = getobs(data, 1, obsdim) # バッファを事前に割り当てるために最初の要素を使用
for _ in obsview(data, obsdim)
    getobs!(obs, _) # 各反復でバッファを再利用
    # ...
end
```

詳細については[`BufferGetObs`](@ref)、[`obsview`](@ref)、および[`getobs!`](@ref)を参照してください。また、ミニバッチバージョンについては[`eachbatch`](@ref)も参照してください。
