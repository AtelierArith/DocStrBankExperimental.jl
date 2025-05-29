```
DMTest(rejH0::Int, pvalue::Float64, bestinput::Int, teststat::Float64, dmmethod::DMMethod)
```

Diebold-Marianoテストの出力タイプ。フィールドの説明は以下の通りです：

```
rejH0 <- 帰無仮説が棄却される場合はtrue、そうでない場合はfalse
pvalue <- テストからのp値
bestinput <- 予測1がより正確な場合は1、予測2がより正確な場合は2。予測1と2の定義については?dmを参照してください。
teststat <- dmmethod == :hac の場合はHAC分散でスケーリングされた損失差の平均
            dmmethod == :boot の場合は損失差の平均
dmmethod <- テストで使用されるDiebold-Marianoメソッド。詳細については?DMMethodを参照してください。
```
