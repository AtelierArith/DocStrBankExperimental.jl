```
Hessian(model; chunck_size)
```

現在のパラメータ値における `neural_choiceDDM` の負の対数尤度のヘッセ行列を計算します。

引数:

  * `model`: `neural_choiceDDM` のインスタンス

オプションの引数:

  * `chunk_size`: ヘッセ行列を計算するために必要な対数尤度のパス数を管理するパラメータ。より多くのメモリにアクセスできる場合は、大きくすることができます。
