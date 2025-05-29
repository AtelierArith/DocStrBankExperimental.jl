```
EvalOptions
```

これは、評価バックエンドなどの式評価のオプションを保持します。

# フィールド

  * `turbo::Val{T}=Val(false)`: `Val{true}`の場合、より高速な評価のためにLoopVectorization.jlを使用します。
  * `bumper::Val{B}=Val(false)`: `Val{true}`の場合、より高速な評価のためにBumper.jlを使用します。
  * `early_exit::Val{E}=Val(true)`: `Val{true}`の場合、任意のステップの任意の要素が`NaN`または`Inf`になると計算が終了します。`eval_tree_array`の場合、これにより2番目の戻り値である完了フラグが`false`になります。`tree(X)`を使用して式を呼び出す場合、これにより`NaN`がバッファ全体を埋めることになります。この早期終了は、計算サイクルの無駄を避けるために行われます。`Val{false}`を設定すると、通常通り計算が続行され、実際に`NaN`を持つ要素にのみ`NaN`が結果として現れます。
  * `buffer::Union{ArrayBuffer,Nothing}`: `nothing`でない場合、このバッファを評価に使用します。これは、`array`フィールドと、どのバッファスロットを使用するかを反復するために使用される`index`フィールドを持つ`ArrayBuffer`のインスタンスである必要があります。
