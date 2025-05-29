```
get_fluid_param_string(fluid::AbstractString, param::AbstractString)
```

流体から値の文字列を取得します（流体の数値はProps1SI関数から取得できます）。

# 引数

  * `fluid`: CoolPropの一部である流体の名前、例えば「n-プロパン」
  * `param`: 次の表に記載されている用語のいずれかの形式の文字列

| ParamName                     | 説明                                          |
|:----------------------------- |:------------------------------------------- |
| "aliases"                     | 流体のエイリアスのカンマ区切りリスト                          |
| "CAS", "CAS_number"           | CAS番号                                       |
| "ASHRAE34"                    | ASHRAE標準34の安全評価                             |
| "REFPROPName", "REFPROP_name" | REFPROPで使用される流体の名前                          |
| "Bibtex-XXX"                  | BibTeXキー、XXXはget_BibTeXKeyで使用されるbibtexキーの1つ |
| "pure"                        | 流体が純粋であれば「true」、そうでなければ「false」              |
| "formula"                     | 利用可能な場合は流体の化学式をLaTeX形式で、そうでなければ""           |

# 注意

この関数の表形式の出力は`?CoolProp_fluids`で利用可能です。
