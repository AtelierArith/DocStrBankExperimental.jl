```
recursive_copyto!(x, y)
```

二重構造体 `x` と `y` の葉を再帰的にコピーします。Functor 言語では、これは `fmap(copyto!, x, y)` を行うことに相当しますが、この実装は一般的なケースに対して型安定なコードを使用しています。変更不可能な葉はエラーを引き起こすことに注意してください。

!!! warning "非推奨警告"
    Lux v1.3.0 から、この関数は `Functors.fmap` に代わって非推奨となります。Functors v0.5 は `fmap` のパフォーマンスを大幅に改善しましたので、この関数は非推奨となりました。ユーザーは代わりに `Functors.fmap` を使用することを推奨します。

