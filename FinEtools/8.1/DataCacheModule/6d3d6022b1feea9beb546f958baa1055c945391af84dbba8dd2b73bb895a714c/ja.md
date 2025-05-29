```
DataCache{D, F<:Function}
```

データをキャッシュするための型、ベクトル、行列、数値など。

`D` = データの型、例えば `Matrix{Float64}` または `Float32`。`F` = 配列のエントリを更新するための関数の型。

キャッシュを配列の値で埋めるための関数のシグネチャは次のとおりです：

```
function fillcache!(cacheout::D,
    XYZ::AbstractVecOrMat{<:Real}, tangents::AbstractMatrix{<:Real},
    feid::IT, qpid::IT) where {D, T, IT}
    ... # cacheoutの値を修正する
    return cacheout
end
```

`XYZ`の位置を使用することができ、要素のヤコビ行列の列である`tangents`を使用することができ、有限要素識別子（すなわち、シリアル番号）である`feid`の値を選択することもでき、積分点の識別子（すなわち、シリアル番号）である`qpid`の値を選択することもできます。これらの値は、キャッシュの値を要求するコードによって提供されます。修正された引数`cacheout`を返す必要があります。

キャッシュにアクセスされると、コールバック`fillcache!`が呼び出され、出力`cacheout`はキャッシュデータの値で埋められます。

# 例

```
function fillcache!(cacheout::Array{CT, N},
        XYZ::AbstractVecOrMat{<:Real}, tangents::AbstractMatrix{<:Real},
        feid::IT, qpid::IT) where {CT, N, T, IT}
    cacheout .= LinearAlgebra.I(3)
    return cacheout
end
c = DataCache(zeros(Float32, 3, 3), fillcache!)
function f(c)
    XYZ, tangents, feid, qpid = (reshape([0.0, 0.0], 1, 2), [1.0 0.0; 0.0 1.0], 1, 1)
    data = c(XYZ, tangents, feid, qpid)
end
@test f(c) == LinearAlgebra.I(3)
```

!!! note
    データキャッシュのポイントは、データのコピーが行われないことです。キャッシュデータフィールドは埋められ、返されますが、データをコピーする必要はありません。悪いニュースは、キャッシュはスレッドセーフではないことです。読み取りは問題ありませんが、書き込みはデータ競合を引き起こす可能性があります。

