`Unscented`構造体は、`Delta`および`Flow`ファクタノードの近似方法を定義します。より具体的には、シグマポイント計算に使用されるハイパーパラメータを含んでいます。

# 引数

  * `α`: 無香変換のスプレッドパラメータ #1
  * `β`: Deltaノード入力の（非ガウス）分布に関する事前情報を組み込むためのアルゴリズムパラメータ
  * `κ`: 無香変換のスプレッドパラメータ #2
  * `e`: 内部キャッシュ

デフォルトパラメータを持つ`Unscented`構造体は、`Unscented()`として構築できます。

`Unscented`構造体は、`DeltaMeta`または`FlowMeta`構造体内で使用され、次のように含めることができます：

```
    y ~ f(x) where { meta = DeltaMeta(method = Unscented()) }
    # または
    y ~ Flow(x) where { meta = FlowMeta(flowmodel, Unscented()) }
```
