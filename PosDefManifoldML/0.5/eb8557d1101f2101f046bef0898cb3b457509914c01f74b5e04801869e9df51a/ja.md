```julia
    function saveas(object, filename::String)
```

`object`をファイルに保存します。ファイルのフルパスは`filename`として指定されます。これは、例えば[`CVres`](@ref)構造体や[`Pipeline`](@ref)タプルを保存するために使用できます。

**参照**: [`load`](@ref)

**例**

```julia
using PosDefManifoldML, PosDefManifold, Serialization

## クロスバリデーション構造を保存してからロードする

P, _dummyP, y, _dummyy = gen2ClassData(10, 40, 40, 30, 40, 0.15)

cv = crval(MDM(logEuclidean), P, y; scoring=:a)

filename=joinpath(@__DIR__, "mycv.jls")
saveas(cv, filename)

mycv = load(filename)

# クロスバリデーションのp値を取得する
mycv.p

## パイプラインを保存してからロードする

# 'トレーニング'データと`テスト`データを生成する
PTr=randP(3, 20) # 20のランダムな3x3エルミート行列
PTe=randP(3, 5) # 5のランダムな3x3エルミート行列

# パイプラインをフィットさせてトレーニングデータを変換する
p = fit!(PTr, @pipeline Recenter(; eVar=0.99) Compress)

# フィットしたパイプラインを保存する
filename=joinpath(@__DIR__, "pipeline.jls")
saveas(p, filename) 

mypipeline = load(filename)

# ロードしたパイプラインを使用してテストデータを変換する
transform!(PTe, mypipeline)
```
