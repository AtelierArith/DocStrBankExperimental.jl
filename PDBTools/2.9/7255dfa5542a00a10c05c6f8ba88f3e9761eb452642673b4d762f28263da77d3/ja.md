```
select_with_vmd(inputfile::String, selection::String; vmd="vmd", srcload=nothing)
select_with_vmd(atoms::AbstractVector{<:Atom}, selection::String; vmd="vmd", srcload=nothing)
```

VMD選択構文を使用して原子を選択し、バックグラウンドでvmdを実行します。入力はファイルまたは原子のリストであることができます。

選択のインデックス（1ベース）と原子名のリストを含むタプルを返します。

入力ファイル（トポロジー、座標など）から選択を返す関数で、バックグラウンドでVMDを呼び出します。

`srcload`引数は、入力ファイルを読み込む前にスクリプトのリストを読み込むために使用できます。たとえば、カスタム選択キーワードを定義するためのマクロを使用することができます。
