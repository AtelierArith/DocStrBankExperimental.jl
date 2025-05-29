ユーザーの位置を計算します

```julia
user_position(prev_pos, rSats, ρ)
user_position(prev_pos, rSats, ρ, accuracy)

```

´rSats´: 衛星位置の配列。衛星ごとに3つの値（xyz）が必要で、サイズは(3, N)でなければなりません。´ρ´: 擬似距離の配列

最小二乗法によってユーザーの位置を計算します。このアルゴリズムは一般的な受信方法に基づいています。
