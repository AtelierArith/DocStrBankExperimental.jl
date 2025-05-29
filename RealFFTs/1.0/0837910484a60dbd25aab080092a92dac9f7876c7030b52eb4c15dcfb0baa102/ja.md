```
plan = plan_rfft!(RC::RCpair; flags=FFTW.ESTIMATE, timelimit=FFTW.NO_TIMELIMIT)
```

`RC`のデータに対して実数から複素数へのFFTを実行するためのプランを作成します。`plan(RC)`を使用してFFTを実行します。

プランニングは、特定の配列サイズに対して(I)FFTのパフォーマンスを最適化することを可能にします。プランニングに関する詳細はFFTWのドキュメントを参照してください。
