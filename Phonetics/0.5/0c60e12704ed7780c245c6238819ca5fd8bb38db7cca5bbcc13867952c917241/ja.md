```
generateFormants(nTokens; [cats=["iy", "aa", "uw"], gender=["w", "m"]])
```

Hillenbrand et al. (1995, Acoustic characteristics of American English vowels, DOI: 10.1121/1.411872) の観察に基づいて、多変量正規分布から合成フォルマントを生成します。現在、男性を `"m"`、女性を `"w"` として、/i/ を `"iy"`、/ɑ/ を `"aa"`、/u/ を `"uw"` として母音を生成することをサポートしています。Hillenbrand et al. がデータを収集した際、女性の /ɑ/ トークンから1つの観察が除外されました。なぜなら、F2値が測定できなかったためです。平均ベクトルと共分散行列の値は小数点以下2桁に丸められています。

# 引数

  * `nTokens` 各カテゴリおよび性別のペアリングに対して生成するトークンの数
  * `cats` (キーワード引数) トークンを生成するための母音カテゴリのベクトル
  * `gender` (キーワード引数) トークンを生成するための性別カテゴリのベクトル
  * `seed` 再現可能な結果を得るための `MersenneTwister` 擬似乱数生成器のシード値; デフォルト値の `nothing` を使用すると、システム生成の乱数シードが使用されます。
  * `rng` 擬似乱数生成に使用する `AbstractRNG` オブジェクト; デフォルト値の `nothing` を使用すると、`MersenneTwister` オブジェクトが作成されます。
