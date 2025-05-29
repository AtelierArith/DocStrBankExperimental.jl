```
process_userrecipe!(plt, attributes_list, attributes)
```

プロットパッケージ特有のポストプロセッシングを行い、attributes*listにシリーズ属性を追加します。例えば、Plotsは`plt`のシリーズ数を増やし、attributesに`:series*plotindex`を設定し、エラーバーやスムーズのための新しいシリーズ属性を追加する可能性があります。
