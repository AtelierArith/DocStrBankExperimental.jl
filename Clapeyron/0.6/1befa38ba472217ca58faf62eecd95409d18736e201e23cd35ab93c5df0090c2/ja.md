```
gibbs_duhem(model,V,T,z=[1.0])
```

は入力条件に対してギブス-デュヘムチェックを実行します：

```
∑zᵢμᵢ - G ≈ 0
```

ここで `G` は全体のギブスエネルギーです。ユーザー定義のEOSが一貫しているかどうかを診断するのに役立ちます。

指定された条件で |∑zᵢμᵢ - G|、∑zᵢμᵢ および G を返します。
