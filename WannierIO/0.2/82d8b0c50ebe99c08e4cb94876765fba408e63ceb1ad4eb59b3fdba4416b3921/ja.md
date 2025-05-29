```
read_amn(filename)
read_amn(filename, ::FortranText)
read_amn(filename, ::FortranBinaryStream)
```

wannier90の`amn`ファイルを読み込みます。

# 戻り値

  * `A`: 長さ-`n_kpts`のベクトルで、各要素は`n_bands * n_wann`の行列です。
  * `header`: ファイルの最初の行

この関数には3つのバージョンがあります：1つ目はラッパー関数で、ファイルの形式（テキストまたはバイナリ）を自動的に検出し、A行列の次元についてユーザーに迅速なヒントを提供するために追加の整形出力を行います；内部的には、実際の読み込みのために2番目または3番目のバージョンを呼び出します。

Wannier90は`amn`のFortranテキスト形式のみを持っていますが、ディスクスペースを節約するためにFortranストリームIOを使用してFortranバイナリ形式を出力できるQE pw2wannier90.xのカスタムバージョンを作成しました。1つ目の関数はファイル形式を自動的に検出するため、ユーザーにとっては透過的です。
