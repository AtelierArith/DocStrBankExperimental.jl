```
colorscheme(scheme)
```

後続のプロットのカラースキームを設定します。

スキームの値は、以下の数字または文字列のいずれかです：

  * 0: `"none"`
  * 1: `"light"`
  * 2: `"dark"`
  * 3: `"solarized light"`
  * 4: `"solarized dark"`

スキームは、`colorscheme`を呼び出した後に描画されるすべてのプロットに適用されます。たとえそれらが事前に作成されていてもです。特定のスキームを特定のプロットや図に適用するには、[`colorscheme!`](@ref)を使用します。

スキームが`"none"`（`0`）の場合、標準スキームが設定されます。これは`"light"`（1）と同じですが、図のデフォルトの背景が透明です。

# 例

```julia
# サンプルデータを作成
x = LinRange(0, 3, 20)
y = [sin.(x) exp.(-x)]
# 新しいカラースキームを設定し、データをプロット
subplot(1,2,1)
colorscheme("light")
plot(x, y)
# 特定のスキームで2つ目のプロットを作成
subplot(1,2,2)
plot(x, y, scheme=3) # solarized light
# さて、グローバルスキームを変更し、再描画
# （これは最初のプロットにのみ影響します）
colorscheme("solarized dark")
draw(gcf())

```
