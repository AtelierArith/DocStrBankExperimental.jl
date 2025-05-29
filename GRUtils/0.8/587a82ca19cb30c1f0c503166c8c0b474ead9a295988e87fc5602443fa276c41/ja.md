```
xflip(flag)
yflip(flag)
zflip(flag)
```

X軸、Y軸、またはZ軸の方向を反転させます（`flag == true`）、または元の方向に戻します（`flag == false`）。

プロット関数でキーワード引数 `xflip=<true/false>` などを使用して、プロット作成時に反転した軸を設定します。

# 例

```julia
# x軸を反転させる
xflip(true)
# y軸が反転していないことを確認する
yflip(false)
```
