```
movie_from_images(; dir=pwd(), file=nothing, outfile=nothing, framerate=10, copy_to_current_dir=true, type=:mp4_default, collect=true)
```

`Paraview`を使用してアニメーションを作成する一般的な方法は、`Save Animation`オプションを使用して一連の`*.png`画像を保存することです。

この関数は、これらの画像を`*.mp4`ムービーに結合します。

# オプション

  * `dir`:    画像が保存されているディレクトリ。
  * `file`:   拡張子と番号なしの画像シリーズのファイル名。同じディレクトリに>1の画像シリーズが保存されている場合は必須。デフォルトでは、利用可能なファイルからこの名前を再構築します。
  * `outfile`:  拡張子なしの結果のムービーのファイル名; 指定されていない場合は、`file`が使用されます。
  * `framerate`: フレーム/秒の数。
  * `copy_to_current_dir`: `true`の場合、最終ムービーを現在のディレクトリにコピーします（デフォルト）。そうでない場合は、`dir`に保存されます。
  * `type`: 作成されるムービーのタイプ; 可能なオプションは：

      * `:mp4_default`: よく圧縮された`mp4`ムービーを保存するデフォルトオプションで、iPadやPowerPointプレゼンテーションに埋め込むのに適しています。
      * `:mov_hires`: 高解像度のQuickTimeムービー（ファイルサイズが大きく、Windowsと互換性がありません）
  * `collect`: `true`の場合、`FFMPEG`の出力を抑制します（デフォルト）。
