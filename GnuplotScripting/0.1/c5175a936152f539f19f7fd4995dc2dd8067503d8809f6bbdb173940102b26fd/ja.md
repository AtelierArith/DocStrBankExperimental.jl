```julia
set_title(gp::GnuplotScript,title::AbstractString;
                   enhanced::Bool = false)
```

プロットのタイトルを定義します。`enhanced`がtrueの場合、一部の文字が特別な方法で処理されます。例えば、`_`は下付き文字のテキストです。
