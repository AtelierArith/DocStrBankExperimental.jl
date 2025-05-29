```
prepare_options(library::SpectralLibrary, combination_type::String,
                 num_endmembers::Vector{Int64}, class_idx)
```

指定された組み合わせタイプに基づいてエンドメンバーの組み合わせを準備します。

  * 組み合わせタイプのオプション:

      * `"class-even"`: 各クラスから1つのエンドメンバーが選択されるすべての組み合わせを生成します。
      * `"all"`: `num_endmembers` スペクトルのすべての可能な組み合わせを生成します。
