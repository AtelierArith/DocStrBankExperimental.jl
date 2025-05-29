```
ParamDict(data::Dict, override_dict::Union{Nothing,Dict})
```

TOMLファイルから読み込まれた情報を保持する構造体であり、パラメータ化タイプ`FT`を持ちます。

名前を使って検索します。

# フィールド

  * `data`: デフォルト/マージされたパラメータTOMLファイルを表す辞書
  * `override_dict`: 何もないか、オーバーライドパラメータTOMLファイルを表す辞書
