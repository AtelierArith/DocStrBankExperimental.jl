```
AbstractZero <: AbstractTangent
```

ゼロのようなタンジェントのスーパークラス—すなわち、他の値に加算または乗算したときにゼロのように振る舞うタンジェント。ADシステムが`AbstractZero`のサブタイプのみを入力として受け取る伝播器に遭遇した場合、AD操作を実行するのを停止できます。すべての伝播器は線形関数であり、したがって最終結果はゼロになります。

すべての`AbstractZero`のサブタイプはシングルトン型です。それらは[`ZeroTangent()`](@ref)と[`NoTangent()`](@ref)の2つです。
