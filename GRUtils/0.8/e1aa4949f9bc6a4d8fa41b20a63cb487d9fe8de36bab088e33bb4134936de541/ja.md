```
background(color[, alpha])
```

現在の図にカスタム背景色を追加します。

引数は16進数の色コードまたは透明な背景のための`nothing`であることができます。部分的に透明な色は、2番目の引数として0から1の間のアルファ値を追加することで定義できます。

プロット関数でキーワード引数`backgroundcolor`と`backgroundalpha`を使用して、プロットの作成中に特定の背景色設定を行います。

これは、図に含まれるすべてのプロットの軸と凡例の外側の領域に対して[`colorscheme`](@ref)で定義されたデフォルトの背景を上書きします。個々のサブプロットの背景を変更するには[`background!`](@ref)を使用します。

# 例

```julia
# 薄い青の背景を持つプロットを作成
plot(x, y, backgroundcolor=0x88ccff)
# 背景を削除
background(nothing)
```
