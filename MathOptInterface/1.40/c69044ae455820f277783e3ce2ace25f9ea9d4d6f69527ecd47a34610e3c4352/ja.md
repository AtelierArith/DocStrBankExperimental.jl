```
INVALID_MODEL::TerminationStatusCode
```

[`TerminationStatusCode`](@ref) 列挙型のインスタンスです。

## 概要

アルゴリズムはモデルが無効であるため停止しました。

この戻りコードの理由はソルバー固有ですが、一般的な原因としては、問題に変数や制約がゼロであるか、問題データに `NaN` のような無効な数値が含まれていることがあります。
