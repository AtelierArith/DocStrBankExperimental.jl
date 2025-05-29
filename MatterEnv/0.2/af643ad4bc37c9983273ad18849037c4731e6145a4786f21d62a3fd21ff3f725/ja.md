```
load_procar(filename::String="PROCAR"; spin::Bool=false, noncollinear::Bool=false) -> Projection, KPoints, Bands
```

PROCARファイルから波動関数⟨Yₗₘ|ϕₙₖ⟩の投影をロードします。

# 引数

  * `filename::String="PROCAR"`: 入力ファイルの名前
  * `spin::Bool=false`: ISPIN = 0(false) または 1(true)
  * `noncollinear::Bool=false`: LNONCOLINEAR = 0(false) または 1(true)。noncolinear=1の場合、スピンの値は無視されます。

# コリニアの場合の戻り値

  * `Projection`: 波動関数⟨Yₗₘ|ϕₙₖ⟩の投影
  * `Array{KPoint, 1}`: k点のメタデータ
  * `Bands`: すべてのバンドのメタデータ

# ノンコリニアの場合の戻り値

  * `Projection`: 波動関数⟨Yₗₘ|ϕₙₖ⟩の総投影
  * `Projection`: x軸に沿ったスピンの投影
  * `Projection`: y軸に沿ったスピンの投影
  * `Projection`: z軸に沿ったスピンの投影
  * `Array{KPoint, 1}`: k点のメタデータ
  * `Bands`: すべてのバンドのメタデータ

```
