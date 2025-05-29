```
XPRSiisfirst(prob, mode)::status
```

不適合な問題における不可約不適合集合 (IIS) の検索を開始します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `mode::Integer`: IIS 検索モード: 0は初期の不適合サブ問題を見つけた後に停止; 1はIISを見つけ、IISの単純さを重視; 2はIISを見つけ、迅速な結果を重視。

# 戻り値

  * `status::Int32`: 検索後のステータス: 0成功; 1適合問題; 2エラー; 3タイムアウトまたは中断。

C API の対応する関数 [XPRSiisfirst](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisfirst.html) のドキュメントも参照してください。
