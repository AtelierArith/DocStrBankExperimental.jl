```
squirclepath(cpos, w, h;
    action = :none,
    kappa = 0.75,
    reversepath = false)
```

スクワイアまたはスーパーロップス（基本的には角が丸い長方形）を作成します。中心位置、幅、高さを指定します。

`kappa` は形状の円形度を決定する値（通常は0と1の間）です。`kappa` が `4.0 * (sqrt(2.0) - 1.0) / 3.0`（つまり `0.5522847498307936`）の場合、形状は円の合理的な近似になります。

`reversepath` オプションを使用して、逆方向にパスを構築します。

`squircle()` と `squirclepath()` の違いは、前者が点からポリゴンを構築するのに対し、後者はベジェ曲線を使用してパスを構築することです。

`circlepath()` も参照してください。
