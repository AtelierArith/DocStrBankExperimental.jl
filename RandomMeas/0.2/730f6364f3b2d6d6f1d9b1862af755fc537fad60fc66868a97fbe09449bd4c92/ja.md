```
get_rotation(site_index, ensemble="Haar")
```

指定されたアンサンブルからサンプリングされた単一キュービットユニタリを生成します。

# 引数:

  * `site_index::Index{Int64}`: サイトインデックス。
  * `ensemble::String`: ユニタリアンサンブルのタイプ（`"Haar"`、`"Pauli"`、`"Identity"`）。

# 戻り値:

  * ユニタリ変換を表す `ITensor`。

# 例:

```julia
U = get_rotation(site_index, "Pauli")
```
