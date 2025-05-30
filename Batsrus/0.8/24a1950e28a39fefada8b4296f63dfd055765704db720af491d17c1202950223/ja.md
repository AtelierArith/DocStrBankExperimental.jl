```
 convertIDLtoVTK(filename; gridType=1, verbose=false)
```

3D BATSRUS *.out を VTK に変換します。`filename` が "out" で終わらない場合、同じ名前のタグを持つ ".info" および ".tree" ファイルを探し、3D 非構造化 VTU ファイルを生成します。

# キーワード

  * `gridType::Symbol`: 目標 VTK グリッドのタイプ (vti: 画像, vtr: 直交, vts: 構造化グリッド)。
