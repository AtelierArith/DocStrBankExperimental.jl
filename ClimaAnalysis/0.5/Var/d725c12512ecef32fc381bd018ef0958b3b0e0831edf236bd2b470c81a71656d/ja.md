```
OutputVar(path,
          short_name = nothing;
          new_start_date = nothing,
          shift_by = identity)
```

`path`にあるNetCDFファイルを`OutputVar`として読み込みます。

`short_name`が`nothing`の場合、自動的に名前を見つけます。

時間次元の日付は、時間次元配列の最初の日付または`new_start_date`に関して自動的に秒に変換されます。パラメータ`new_start_date`は、[Dates](https://docs.julialang.org/en/v1/stdlib/Dates/)モジュールで解析可能な任意の文字列または`Dates.DateTime`オブジェクトであることができます。パラメータ`shift_by`は、`Dates.DateTime`要素を受け取り、`Dates.DateTime`要素を返す関数です。開始日付は`OutputVar`の属性に追加されます。パラメータ`shift_by`は、`Dates.DateTime`要素を受け取り、`Dates.DateTime`要素を返す関数です。この関数は、時間配列の各要素に適用されます。日付のシフトと秒への変換は、その順序で行われます。
