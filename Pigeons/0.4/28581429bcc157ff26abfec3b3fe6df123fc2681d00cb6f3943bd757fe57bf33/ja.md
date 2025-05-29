```julia
watch(result; machine, last, interactive)

```

指定された `machine` のキューの状態と標準出力およびエラーストリーム（統合されたもの）を表示します。

注意: interactive = true の場合に control-c を使用すると、バージョン 1.8 以降の Julia はクラッシュする傾向があります。
