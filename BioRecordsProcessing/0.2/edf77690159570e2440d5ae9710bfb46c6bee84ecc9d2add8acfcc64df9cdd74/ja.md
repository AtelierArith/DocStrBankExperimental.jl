```julia
File(filename; second_in_pair = nothing)
```

ペアファイルの場合、ペアの最初のファイルのファイル名を引数として受け取り、2番目のファイルのファイル名を返す関数を提供できます。たとえば、`replace`や辞書を使用することができます。例: `second_in_pair = f1 -> replace(f1, "_1" => "_2")`。
