```
grow!(A, B, prepend=false) -> A
```

リサイズ可能な配列 `A` を `B` の要素で拡張し、`A` を返します。`prepend` が `true` の場合、`B` の要素は `A` の前に挿入されます。それ以外の場合、`B` の要素は `A` の後に追加されます。デフォルトでは、`prepend` は `false` です。

`A` が `N` 次元を持つと仮定すると、配列 `B` は `N` または `N-1` 次元を持つことができます。`A` と `B` の最初の `N-1` 次元は同一でなければならず、結果の最初の次元になります。`B` が `A` と同じ数の次元を持つ場合、結果の最後の次元は `A` と `B` の最後の次元の合計になります。それ以外の場合、結果の最後の次元は `A` の最後の次元に 1 を加えたものになります。

引数 `prepend` に応じて、`grow!` メソッドを呼び出すことは `append!` または `prepend!` メソッドを呼び出すことと同等です。

詳細は [`ResizableArray`](@ref) を参照してください。
