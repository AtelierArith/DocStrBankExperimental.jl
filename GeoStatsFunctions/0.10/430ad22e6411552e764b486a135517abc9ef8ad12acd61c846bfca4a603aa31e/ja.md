```
surfplot(f; [options])
```

与えられた `options` で地質統計的な表面 `f` をプロットします。

## 一般的なオプション

  * `colormap` - カラーマップ
  * `maxlag`   - 最大ラグ
  * `labels`   - 変数名

## 理論的関数オプション

  * `normal` - 平面への法線方向（デフォルトは垂直）
  * `nlags`  - ラグの数（デフォルトは `20`）
  * `nangs`  - 角度の数（デフォルトは `50`）

## 例

```julia
# ガウス変動関数で図を初期化
fig = surfplot(GaussianVariogram())

# 図に球状変動関数を追加
surfplot!(fig, SphericalVariogram())
```

### 注意

この関数は、Julia v1.9 以降の言語のパッケージ拡張を介して Makie.jl バックエンドが存在する場合にのみ機能します。
