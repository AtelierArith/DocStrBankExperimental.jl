```
xticks(minor[, major = 1])
yticks(minor[, major = 1])
zticks(minor[, major = 1])
```

X、Y、またはZ軸の目盛りの`minor`間隔を設定し、（オプションで）`major`目盛りの間の`minor`目盛りの数を設定します。

プロット関数で目盛りの間隔を設定するには、キーワード引数`xticks=(minor, major)`などを使用します（この場合、minorとmajorの両方の値が必要です）。

# 例

```julia
# X軸の0.2単位ごとのマイナー目盛り
xticks(0.2)
# Y軸の1単位ごとのメジャー目盛り（5つのマイナー目盛り）
yticks(0.2, 5)
```
