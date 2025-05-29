```
find_hall_number(hallsymbol::AbstractString, hm::AbstractString=hallsymbol, it::Integer=0, warnonnotfound=false)
```

与えられた `hallsymbol` に対応するホール番号を決定します。ヘルマン-マウグイン記号 `hm` を代わりに使用することもできますし、単に空間群の国際表番号 `it` を使用して、群の標準設定のホール番号を取得することもできます。

`hallsymbol` または `hm` に空の文字列を渡すか、`it` に 0 を渡すと、その引数は無視されます。

オプションの引数 `warnonnotfound` は、提供された引数のいずれかが認識されなかった場合に警告を表示するかどうかを指定します。
