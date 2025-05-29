```
XPRS_MIPABSGAPNOTIFYOBJ
```

分岐と境界: `gapnotify` コールバックが XPRSaddcbgapnotify を使用して設定されている場合、このコールバックは、最良の解の値が設定した `MIPRELGAPNOTIFYOBJ` 制御の値に達するかそれを超えたときにツリー検索中にトリガーされます。(double)

デフォルト値: `-1.0E+20` (最小化問題の場合); `1.0E+20` (最大化問題の場合)

ドメイン: [-1E+40,+1E+40]
