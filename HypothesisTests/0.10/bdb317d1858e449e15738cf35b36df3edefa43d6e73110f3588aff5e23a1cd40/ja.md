```
confint(test::BinomialTest; level = 0.95, tail = :both, method = :clopper_pearson)
```

バイナリ比率の信頼区間を、以下のいずれかの方法を使用して計算します。`method`の可能な値は次のとおりです。

  * `:clopper_pearson`（デフォルト）：Clopper-Pearson区間は、バイナリ分布に基づいています。経験的カバレッジは、名目上のカバレッジ`level`よりも少なくなることはなく、通常は保守的すぎます。
  * `:wald`：Wald（または正規近似）区間は、実際のバイナリ分布の標準近似に依存します。成功確率がゼロまたは1に近い場合、カバレッジは不安定に悪くなる可能性があります。
  * `:wilson`：Wilsonスコア区間は、正規近似に依存します。`:wald`とは異なり、標準偏差は経験的推定によって近似されず、小さなサンプル数や極端な成功確率でも良好な経験的カバレッジを得ることができます。
  * `:jeffrey`：Jeffreys区間は、非情報的Jeffreys事前を使用して得られるベイズの信頼区間です。この区間はWilson区間に非常に似ています。
  * `:agresti_coull`：Agresti-Coull区間は、Wilson区間の簡略版であり、両者は同じ値の周りに中心を持っています。Agresti Coull区間は、より高いまたは同等のカバレッジを持っています。
  * `:arcsine`：確率$p$に対して$var(p)$を独立にするために、アークサイン変換を使用して計算された信頼区間。

# 参考文献

  * Brown, L.D., Cai, T.T., and DasGupta, A. バイナリ比率の区間推定。Statistical Science, 16(2):101–117, 2001。

# 外部リンク

  * [ウィキペディアのバイナリ信頼区間](https://en.wikipedia.org/wiki/ Binomial_proportion_confidence_interval)
