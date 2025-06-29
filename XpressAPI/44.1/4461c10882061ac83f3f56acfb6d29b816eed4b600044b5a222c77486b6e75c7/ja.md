```
XPRS_MULTIOBJOPS
```

マルチオブジェクティブ問題を解決する際の最適化プログラムの動作を変更します。（整数）

デフォルト値： `7`（すべてのビットが設定されています）

値はビットセットです：ビット 0 : `XPRS_MULTIOBJOPS_ENABLED`マルチオブジェクティブが有効です。このビットが設定されていない場合、マルチオブジェクティブ問題はシングルオブジェクティブ問題として扱われ、目的 `0` のみが最適化されます。ビット 1 : `XPRS_MULTIOBJOPS_PRESOLVE`プレソルブ中にマルチオブジェクティブの変更を適用します。このビットが設定されていない場合、元の問題は各後続の目的を解決する際に変更され、これらの変更は解決が完了した後も問題に残ります。ビット 2 : `XPRS_MULTIOBJOPS_RCFIXING`削減コストの固定です。このビットが設定されている場合、非基本変数のゼロでない削減コストをその境界に固定することで、以前の目的の最適性が保持されます。設定されていない場合、以前の目的の最適性は問題に制約を追加することで保持されます。
