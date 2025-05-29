```
CSys(sdim::IT1, mdim::IT2, computecsmat::F) where {F <: Function, IT1, IT2}
```

回転行列を計算する関数が与えられたときに座標系を構築します。

関数のシグネチャ：

```
update!(
        csmatout::AbstractMatrix{<:Real},
        XYZ::AbstractVecOrMat{<:Real},
        tangents::AbstractMatrix{<:Real},
        feid::Integer,
        qpid::Integer,
    ) 
```

ここで

  * `csmatout`= 出力行列バッファ、サイズは `(sdim, mdim)`
  * `XYZ`= 物理座標での位置、
  * `tangents`= 接線ベクトル行列、要素内のパラメトリック座標曲線への接線、
  * `feid`= 有限要素識別子；
  * `qpid`= 積分点識別子。

# 例

```
# 円筒座標系：全くメモリを割り当てない！
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
