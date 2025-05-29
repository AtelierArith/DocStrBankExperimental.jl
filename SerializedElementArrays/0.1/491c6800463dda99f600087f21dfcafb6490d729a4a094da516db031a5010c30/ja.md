```
SerializedElementArrays.disk(array::AbstractArray; cleanup=true, path=tempdir())
```

`AbstractArray` `array`をディスク上に保存された`SerializedElementArrays.SerializedElementArray`型の配列に変換します。配列の各要素は、ランダムに生成されたディレクトリ内の個別のファイルにシリアライズ形式で保存されます。

`SerializedElementArray`型の`array`が入力された場合、これは単に元の`array`を返します（`SerializedElementArray`型への変換のように機能します）。キーワード引数は無視されます。

# 引数

  * `array::AbstractArray`: ディスク上に保存された`SerializedElementArrays.SerializedElementArray`に変換する配列。

# キーワード

  * `cleanup::Bool=true`: プロセスが終了したときに返されたパスを自動的に削除しようとするかどうかを制御します。
  * `path=tempdir()`: 配列の要素が保存される一時ディレクトリが作成されるパスのルート。`tempname`関数によって割り当てられたランダムな名前のディレクトリが使用されます。

!!! compat "Julia 1.4"
    これは、配列の要素が保存される一時ディレクトリを作成するためにJulia関数`tempname`を使用します。`tempname`は、パスのカスタマイズとファイルの自動クリーンアップをJulia 1.4以降でのみサポートしています。`path`および`cleanup`引数はJulia 1.4以降でのみサポートされており、それ以前のバージョンでは`cleanup=false`および`path=tempdir()`がデフォルトとなります。

