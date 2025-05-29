```
MergeGreedy <: CodeSimplifier
MergeGreedy(; threshhold=-1e-12)
```

最適化ツールの呼び出し時間を短縮するための収縮コード簡素化ツールで、マージされたテンソルの空間複雑性が減少する場合（差が `threshhold` より小さい場合）に、テンソルを貪欲にマージします。
