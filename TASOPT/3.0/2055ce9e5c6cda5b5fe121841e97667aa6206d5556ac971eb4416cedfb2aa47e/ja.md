```
generate_par_indname(par_suffix::String)
```

は、`index.inc` で宣言され、グローバルスコープで見つかるインデックスを名前にマッピングする、par_array インデックスの変数名を含むベクトルを生成します。

例:

```@example par_indname
    using TASOPT
    # igRange = 1 (from `index.inc`)

    parg_indname = generate_par_indname("g")
    parg_indname[1]
```

!!! details "🔃 入力と出力"
    **入力:**

      * `par_suffix::String`: par 配列のサフィックス (例: "g" は "parg" のための),

    **出力:**

      * `par_indname::Vector{String}`: インデックス変数名に対応するエントリを持つ文字列のベクトル

