```
XPRSaddcbusersolnotify(prob, cb, priority)
```

# 引数

  * `cbprob`: コールバック関数 `usersolnotify` に渡される問題。
  * `solname`: XPRSaddmipsol を使用して最適化ツールに読み込まれたときにソリューションに割り当てられた文字列名。
  * `status`: 次のいずれかのステータス値の1つ：0 ソリューションの処理中にエラーが発生しました。 (`XPRS_USERSOLSTATUS_ERROR`) 1 ソリューションは実行可能です。 (`XPRS_USERSOLSTATUS_ACCEPTED_FEASIBLE`) 2 固定された MIP エンティティで再最適化した後、ソリューションは実行可能です。 (`XPRS_USERSOLSTATUS_ACCEPTED_OPTIMIZED`) 3 ローカルサーチヒューリスティックが適用され、実行可能なソリューションが発見されました。 (`XPRS_USERSOLSTATUS_SEARCHED_SOL`) 4 ローカルサーチヒューリスティックが適用されましたが、実行可能なソリューションは見つかりませんでした。 (`XPRS_USERSOLSTATUS_SEARCHED_NOSOL`) 5 ソリューションは実行不可能で、ローカルサーチを適用できませんでした。 (`XPRS_USERSOLSTATUS_REJECTED_INFEAS_NOSEARCH`) 6 ソリューションは部分的で、ローカルサーチを適用できませんでした。 (`XPRS_USERSOLSTATUS_REJECTED_PARTIAL_NOSEARCH`) 7 提供されたソリューションに固定された MIP エンティティで問題を再最適化できませんでした。おそらく、時間または反復制限に達したためです。 (`XPRS_USERSOLSTATUS_REJECTED_FAILED_OPTIMIZE`) 8 ソリューションは破棄されました。これは、MIP 問題が変更されたり、ソリューションが処理される前に完了するまで解決された場合に発生する可能性があります。 (`XPRS_USERSOLSTATUS_DROPPED`) 9 ソリューションは現在の MIP カットオフ値よりも悪いです。 (`XPRS_USERSOLSTATUS_REJECTED_CUTOFF`)

`cb` は次のシグネチャで呼び出されます：

```
cb(cbprob, solname, status)::Nothing
```
