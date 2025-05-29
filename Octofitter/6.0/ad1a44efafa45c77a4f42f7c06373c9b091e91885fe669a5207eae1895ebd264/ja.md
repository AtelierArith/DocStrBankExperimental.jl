```
HipparcosIADLikelihood(;hip_id)
```

ヒッパルコスIAD尤度をロードします。デフォルトでは、van Leeuwanの還元の抽出されたJava Tool版を取得してキャッチします。

追加の引数：

  * `catalog`: データディレクトリへのパス。デフォルトでは、オンラインから取得してキャッシュします。
  * `renormalize=true`: Nielsen et al. (2020) に従って不確実性を再正規化します。
  * `attempt_correction=true`: G. Brandt et al. (2021) に従って、破損したスキャンのアドホック修正を行います。
  * `is_van_leeuwen=true`: 例えば1997年の還元を使用する場合はfalseに設定します。これは残差の再構築方法に影響します。1997年版は高RV星に時間変化する視差を適用しましたが、van Leeuwanの還元は適用しませんでした。van Leeuwanの還元の残差は、7または9パラメータモデル（該当する場合）に対して相対的ですが、1997年版は常に5パラメータ解に対して相対的であり、高次の項が報告されている場合でもそうです。
