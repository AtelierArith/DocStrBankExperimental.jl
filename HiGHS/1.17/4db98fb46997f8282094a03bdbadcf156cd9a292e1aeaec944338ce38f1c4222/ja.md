```
Highs_feasibilityRelaxation(highs, global_lower_penalty, global_upper_penalty, global_rhs_penalty, local_lower_penalty, local_upper_penalty, local_rhs_penalty)
```

LP/MIPにおける（許容される）非実現可能性の（重み付けされた）合計に対応する解を計算します。

ローカルペナルティが定義されていない場合はNULLを渡し、グローバルペナルティが使用されます。負のペナルティ値は、境界またはRHS値が違反されることができないことを示します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `const`: double global*lower*penalty 変数の下限を違反するためのペナルティ
  * `const`: double global*upper*penalty 変数の上限を違反するためのペナルティ
  * `const`: double global*rhs*penalty 制約RHS値を違反するためのペナルティ
  * `const`: double* local*lower*penalty 変数の特定の下限を違反するためのペナルティ
  * `const`: double* local*upper*penalty 変数の特定の上限を違反するためのペナルティ
  * `const`: double* local*rhs*penalty 特定の制約RHS値を違反するためのペナルティ

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
