```
SurfaceNormal{F<:Function}
```

外部表面法線タイプ。

法線ベクトルは単位長さに正規化されていると仮定されます。

任意の点 `XYZ` での単位法線の値を計算するための関数のシグネチャ。要素のヤコビアン行列の列 `tangents`、有限要素ラベル `feid`、および積分点の識別子 `qpid` を使用します：

```
function computenormal!(normalout::Vector{CT}, XYZ::AbstractVecOrMat{<:Real},
    tangents::AbstractMatrix{<:Real}, feid::IT, qpid::IT) where {CT, IT}
    # 法線を計算し、バッファにコピーします....
    return normalout
end
```

バッファ `normalout` は法線ベクトルの値で満たす必要があります。

キャッシングの詳細については [`DataCache`](@ref) を参照してください。
