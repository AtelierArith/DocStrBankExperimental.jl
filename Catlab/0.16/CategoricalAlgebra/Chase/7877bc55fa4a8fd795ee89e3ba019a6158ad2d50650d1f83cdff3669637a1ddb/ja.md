```
chase(I::ACSet, Σ::AbstractDict, n::Int)
```

埋め込まれた依存関係のリストが与えられた場合、C-SetまたはC-Relインスタンスを追跡します。これは終了しない可能性があるため、反復回数に対する上限`n`が必要です。

```
[,]
```

ΣS  ⟶ Iₙ ⊕↓      ⋮  (結果の射)  ΣT ... Iₙ₊₁

アクティブトリガーごとにSとTのコピーがあります。トリガーはSから現在のインスタンスへのマップです。「アクティブ」である理由は、TからIへの射が存在せず、三角形が可換になるからです。

各反復は上記のプッシュアウト四角形を構築します。結果は射であるため、追跡された結果内の元のCSetインスタンスの起源を追跡できます。

結果が成功によるものかタイムアウトによるものかは、ブールフラグとして返されます。

TODO: このアルゴリズムはホモモルフィズムキャッシングによってより効率的にすることができます。
