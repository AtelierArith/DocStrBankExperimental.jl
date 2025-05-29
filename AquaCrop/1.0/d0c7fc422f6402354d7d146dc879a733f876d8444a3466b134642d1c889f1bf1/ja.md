```
cropfield, all_ok = start_cropfield(; kwargs...)
```

`cropfield::AquaCropField`を適切なruntypeで開始します。これらの`kwargs`が欠けている場合、`runtype`と`parentdir`のデフォルト値を使用します。

作物、土壌などのデフォルト値を持つ`cropfield`を返します。この関数を呼び出した後、`all_ok.logi == true`であるか確認してください。
