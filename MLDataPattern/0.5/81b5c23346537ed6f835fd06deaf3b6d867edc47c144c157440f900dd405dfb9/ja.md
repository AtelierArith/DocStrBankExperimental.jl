```
eachbatch(data, [size], [count], [obsdim])
```

`data`を1バッチずつ反復処理します。`data`の型がサポートしている場合、メモリ効率のためにバッファが事前に割り当てられ再利用されます。

重要: `collect`の使用は避けてください。一般的に、各反復で同じオブジェクトが変更された値を返す可能性があります。そのような動作が望ましくない場合は、代わりに`BatchView`を使用してください。

（定数の）バッチサイズは、`size`を直接指定するか、`count`を使用して間接的に指定することができます。`count`は`nobs`に基づいて`size`を導出します。データセットのサイズが指定された（または推測された）`size`で割り切れない場合、残りの観測値は無視されます。

```julia
X = rand(4,150)
for x in eachbatch(X, size = 10) # または: eachbatch(X, count = 15)
    # ループは15回実行されます
    @assert typeof(x) <: Matrix{Float64}
    @assert size(x) == (4,10)
end
```

配列の場合、観測値は最後の配列次元で表されると仮定されます。これは上書き可能です。

```julia
# 今回は行列の次元を反転させます
X = rand(150,4)
A = eachbatch(X, size = 10, obsdim = 1)
# 挙動は以前と同じです
@assert eltype(A) <: Array{Float64,2}
@assert length(A) == 15
```

複数の変数がサポートされています（例: ラベル付きデータ用）

```julia
for (x,y) in eachbatch((X,Y))
    # ...
end
```

内部的に`eachbatch(data, ...)`は`BufferGetObs(batchview(data, ...))`にマッピングされることに注意してください。

```julia
@assert typeof(eachbatch(X)) <: BufferGetObs
@assert typeof(eachbatch(X).iter) <: BatchView
```

これは、次のコードとほぼ同等です：

```julia
for batch in eachbatch(data, batchsize, obsdim)
    # ...
end
```

おおよそ次のように等価です：

```julia
batch = getobs(data, collect(1:batchsize), obsdim) # バッファを事前に割り当てるために最初の要素を使用
for _ in batchview(data, batchsize, obsdim)
    getobs!(batch, _) # 各反復でバッファを再利用
    # ...
end
```

詳細については[`BufferGetObs`](@ref)、[`batchview`](@ref)、および[`getobs!`](@ref)を参照してください。また、単一観測バージョンについては[`eachobs`](@ref)も参照してください。
