```
Lanczos{N}(a=4)
```

スケールパラメータ `a` と `N` 隣接点にわたるサポートを持つカーネルを介したランツォス再サンプリング。

この形の補間は、サンプルをサイズ `a` のランツォスカーネルで離散畳み込みするだけです。このサイズは、補間が情報をどれだけ「遠く」まで到達するかに直接関連しており、実行時間に `O(N^2)` の影響を与えます。OpenCV の `lanczos4` に一致する代替実装が Lanczos4OpenCV として利用可能です。
