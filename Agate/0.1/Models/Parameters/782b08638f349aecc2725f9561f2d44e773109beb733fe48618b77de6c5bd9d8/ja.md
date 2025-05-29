```
compute_allometric_parameters(plankton::Dict) -> Dict
```

この関数は、     - 各 `plankton` グループ（例: "P", "Z" または "cocco"）のために `n` 個の名前を生成します。       形式は:       `["P1", ..., "P<n>", "Z1", ...., "Z<n>", ...]`     - 各 `plankton` グループのために、線形または対数の分割スケールを使用して `n` 個の直径を生成します。     - 各グループ-直径の組み合わせに対して、出現パラメータ（異形関数、同化行列、       食味行列）をオプションで計算します。     - その他のグループ特有のパラメータを NamedArray に再形成します（例: `linear_mortality`）

すべてのパラメータは次のように返されます:     `Dict(<parameter> => <NamedArray of values>, ....)` グループ名（例: "P"）または最初のステップで生成された名前（例: "P1"）を使用します。

# 引数

  * `plankton`: 次の形式のプランクトングループの特定のパラメータの辞書:      `Dict(<group name> => Dict(<parameter> => <value>, ....), ...)`

    各グループ（例: "P", "Z" または "cocco"）の辞書には、少なくとも   "n" と "diameters" のキーが含まれている必要があります。これらは値の配列または次の形式の辞書です:       `Dict(           "P" => Dict(               "n" => 2,               "diameters" =>                   Dict("min_diameter" => 1, "max_diameter" => 10, "splitting" => "log_splitting"),               ...               ),           "Z" => ...       )`

    各グループの辞書には、オプションで次のキーと値を含めることができます:       - キー: "allometry"（直径依存のパラメータを計算）           - 値: 次の形式の辞書               `Dict(<param name> => Dict("a" => <value>, "b" => <value>), ...)`       - キー: "palatability"（食味行列を生成）           - 値: "can*eat", "optimum*predator*prey*ratio", "protection",             "specificity" キーを持つ辞書       - キー: "assimilation*efficiency"（同化効率行列を生成）           - 値: "can*eat", "can*be*eaten", "assimilation*efficiency" キーを持つ辞書   例えば:       ```       Dict(           "P" => Dict(               ...,               "allometry" => Dict(                   "maximum*growth*rate" => Dict("a" => 2.3148e-5, "b" => -0.15),                   "nutrient*half*saturation" => Dict("a" => 0.17, "b" => 0.27),               ),               ...           ),           "Z" => Dict(               ...,               "palatability" => Dict(                   "can*eat" => 1,                   "optimum*predator*prey*ratio" => 10,                   "protection" => 1,                   "specificity" => 0.3,               ),               "assimilation*efficiency" => Dict(                   "can*be*eaten" => 0,                   "can*eat" => 1,                   "assimilation*efficiency" => 0.32               ),               ...           )       )       ```
