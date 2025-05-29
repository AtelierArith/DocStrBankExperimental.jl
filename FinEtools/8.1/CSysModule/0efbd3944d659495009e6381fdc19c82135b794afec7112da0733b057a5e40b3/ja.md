```
CSys(sdim::IT1, mdim::IT2, z::T, computecsmat::F) where {IT1, IT2, T <: Number, F <: Function}
```

与えられたタイプ `T` の回転行列を計算する関数があるときに座標系を構築します。

  * `z` = ゼロ値、
  * `computecsmat` 関数のシグネチャ:   `update!(           csmatout::AbstractMatrix{<:Real},           XYZ::AbstractVecOrMat{<:Real},           tangents::AbstractMatrix{<:Real},           feid::Integer,           qpid::Integer,       )`   どこで

      * `csmatout`= 出力行列バッファ、サイズ `(sdim, mdim)`;
      * `XYZ`= 物理座標での位置;
      * `tangents`= 要素内のパラメトリック座標曲線に対する接線ベクトル行列;
      * `feid`= 有限要素識別子;
      * `qpid`= 積分点識別子。

# 例

```
# 円筒座標系: 一切のアロケーションなし!
@views function compute!(csmatout, XYZ, tangents, feid, qpid)
    center = (0.0, 0.0, 0.0)
    xyz = (XYZ[1], XYZ[2], XYZ[3])
    csmatout[:, 1] .= xyz .- center
    csmatout[3, 1] = 0.0
    csmatout[:, 1] ./= norm(csmatout[:, 1])
    csmatout[:, 3] .= (0.0, 0.0, 1.0)
    cross3!(csmatout[:, 2], csmatout[:, 3], csmatout[:, 1])
    csmatout[:, 2] ./=  norm(csmatout[:, 2])
    return csmatout
end
```
