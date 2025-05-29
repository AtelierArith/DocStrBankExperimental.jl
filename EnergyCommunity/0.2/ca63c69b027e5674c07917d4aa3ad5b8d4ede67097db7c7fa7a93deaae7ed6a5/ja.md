```
split_financial_terms(ECModel::AbstractEC, profit_distribution)
```

すべてのユーザーによるコスト項の分配を説明する関数。

## パラメータ

  * ECModel : AbstractEC   エネルギーコミュニティモデル
  * profit_distribution   最終目的関数

## 戻り値

```
出力値は、以下の要素を持つNamedTupleです
- NPV: 最終的なprofit_distribution調整に基づく各ユーザーのNPV
ゲーム理論技術による
- CAPEX: 年間化されたCAPEX
- OPEX: 年間化された運営コスト（年間メンテナンスおよび年間ピークおよびエネルギーグリッド料金）
- REP: 年間化された交換コスト
- RV: 年間化された回収料金
- REWARD: ユーザーごとの年間化された報酬分配
- PEAK: 年間化されたピークコスト
- EN_SELL: エネルギー販売からの年間化された収益
- EN_BUY: エネルギー消費および購入からの年間化されたコスト
- EN_NET: 年間化されたネットエネルギーコスト
```
