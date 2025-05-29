```
summary_eigenvalues(
        sm::SmallSignalOutput,
)
```

運転点でのヤコビ行列の固有値の要約を取得するための関数です。各固有値に最も関連する状態、その実部と虚部、減衰および周波数を含むDataFrameを返します。

# 引数

  * `sm::SmallSignalOutput` : 固有値と参加係数を含む小信号出力オブジェクト
