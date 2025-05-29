```
CtGeom{Td,To,Ts}
```

3D CTイメージングのためのレイジオメトリを表す抽象型。

投影ビュー座標は `(s,t)` で、`s` は横断サンプリングを示し、`t` は軸方向（`z` に沿って）を示します。

# 共通フィールド

  * `ns` 各投影ビューのサイズ
  * `nt`
  * `ds` 検出器ピクセル間隔
  * `dt`
  * `offset_s` 単位のない検出器中心オフセット（通常は0または0.25）
  * `offset_t` 単位のない、通常は0
  * `na` 投影ビューの数、別名 nϕ または nβ
  * `orbit` ソースの軌道（度単位またはUnitful）
  * `orbit_start` 開始角度（度単位またはUnitful） `orbit` と `orbit_start` はどちらも単位のない（度）か、同じ単位でなければなりません。
  * `src::CtSource` X線CTソースの軌道を説明します。`CtSourceCircle()` の主なサポート。

# `CtFan` タイプの追加フィールド:

  * `dsd` ソースから検出器までの距離
  * `dod` 原点から検出器までの距離
  * `source_offset` 通常は0

# 単位:

  * `ds`, `dt`, `source_offset`, `dsd`, `dod` はすべて単位のないか、同じ単位でなければなりません。

# 基本メソッド

  * `angles` (na) 度単位
  * `dims (ns, nt, na)`
  * `ones = ones(Float32, ns,nt,na)`
  * `zeros = zeros(Float32, ns,nt,na)`
  * `rays` `(u,v,ϕ,θ)` サンプルのイテレータ
  * `downsample(st, down)` 整数因子でサンプリングを減少させる
  * `oversample(st, over)`
  * `ct_geom_plot3` システムジオメトリをプロット

# 開発者向けの非エクスポートヘルパー関数:

  * `_s (ns) s` サンプル位置
  * `_t (nt) t` サンプル位置
  * `_ws = (ns-1)/2 + offset_s` "中央" サンプル位置
  * `_wt = (nt-1)/2 + offset_t`
  * `_ar (na)` ソース角 [ラジアン]
  * `_rfov` FOV内の最大半径
  * `_zfov` 軸方向FOV
  * `_xds (nb)` 検出器要素の中心 (beta=0)
  * `_yds (nb)` ""
  * `_tau(rg, x, y)` 各 `(x,y)` ペアの投影 s/ds `(length(x), na)`
  * `_shape(rg, proj [,:])` `proj` を配列 `(ns,nt,na[,:])` に再形成
  * `_unitv(rg [, (is,it,ia)])` 単一の非ゼロ要素を持つ単位 'ベクトル'

ファンビームの場合:

  * `_dso = dsd - dod` ソースから原点までの距離（平行ビームの場合はInf）
  * `_dfs` ソースから検出器焦点スポットまでの距離（第3世代CTの場合は0、フラット検出器の場合は`Inf`）
  * `_gamma(rg [,s]) (ns)` ガンマサンプル値 `ラジアン`、オプションで `s` 値を指定
  * `_gamma_max = max(|γ|)` ファン角の半分 `ラジアン`、`offset_s` == 0 の場合
  * `_cone_angle` 軸上の（半分の）コーン角（s=0）：+/- 角度

# 注意

2Dジオメトリには `sino_geom()` を代わりに使用してください。
