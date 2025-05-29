```
create_imagej_macro_here(;MPP::Float64, minimum_segmentation_diameter::Float64)
```

Fijiで`original_video`のバッチセグメンテーション用のマクロスクリプトを作成します。

必要なキーワード引数：

  * `MPP` : ピクセルあたりのマイクロメートル、`Float64`（あなたの顕微鏡設定に特有！）
  * `minimum_segmentation_diameter` : この直径*1.5以上の粒子のみがセグメント化されます、`Float64`。1.5の理由については以下の参考文献を参照してください：

J. Baumgartl, J. L. Arauz-Lara, and C. Bechinger, “Like-charge attraction in confinement: myth or truth?,”   Soft Matter, vol. 2, no. 8, p. 631, 2006, doi: 10.1039/b603052a.

# 例

```julia-repl
julia> create_imagej_macro_here(MPP=0.605, minimum_segmentation_diameter=4.5)
[ Info: ImageJ macro created at ~/tutorial/imagej_macro.ijm. See MicroTracker segmentation docs for instructions on how to use it. 
```
