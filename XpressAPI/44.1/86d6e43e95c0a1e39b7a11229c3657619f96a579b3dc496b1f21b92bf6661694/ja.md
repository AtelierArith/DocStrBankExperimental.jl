```
XPRS_ge_setarchconsistency(consistent)::Nothing
```

さまざまなCPUアーキテクチャ拡張、特に（前）AVXおよびAVX2で同じ実行パスを強制するかどうかを設定します。

# 引数

  * `consistent::Integer`: 同じ実行パスを強制するかどうか: 0同じ実行パスを強制しない（デフォルトの動作）；1同じ実行パスを強制する。

C APIの対応する関数[XPRS*ge*setarchconsistency](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_ge_setarchconsistency.html)のドキュメントも参照してください。
