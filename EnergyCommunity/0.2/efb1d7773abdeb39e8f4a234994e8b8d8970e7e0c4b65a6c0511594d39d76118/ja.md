```
business_plan(ECModel::AbstractEC, profit_distribution)
```

すべてのユーザーによるすべての年のコスト項分布を説明する関数です。

## パラメータ

  * ECModel : AbstractEC   エネルギーコミュニティモデル
  * profit_distribution   最終目的関数
  * user*set*financial   財務分析のために考慮されるユーザーセット

## 戻り値

```
出力値は、次の要素を持つNamedTupleです
- df_business
    ビジネスプラン情報を含むデータフレーム
```
