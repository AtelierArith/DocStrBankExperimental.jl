```
MeasureAutoDiffPerformance(DM::DataModel; modes=diff_backends())
```

与えられた DataModel に対して、さまざまな AD バックエンドのパフォーマンスをテストします。現在ロードされている利用可能なバックエンドについては `diff_backends()` を参照してください。
