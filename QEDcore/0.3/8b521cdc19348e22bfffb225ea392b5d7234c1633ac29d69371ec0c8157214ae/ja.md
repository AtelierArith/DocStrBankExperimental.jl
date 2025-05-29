```
FlatPhaseSpaceLayout{INPSL} <: QEDbase.AbstractOutPhaseSpaceLayout{INPSL}
```

出力粒子の運動量を生成するためのフラットな相空間レイアウトを定義します。このレイアウトは、出力粒子が運動量とエネルギー保存の制約に従って相空間内で均等に分布していると仮定します。これは、RAMBO [Kleiss:1985gy](@cite) (Random Momenta Beautifully Organized) アルゴリズムを利用して運動量を生成することで実現され、質量のない粒子と質量のある粒子の両方をサポートします。

# フィールド

  * `in_psl::INPSL`: プロセスの初期状態レイアウトを提供する入力相空間レイアウト。このフィールドは入力構成にリンクしており、関連する計算間での一貫性を確保するためにアクセス可能です。

# 使用法

`FlatPhaseSpaceLayout` は、高エネルギー物理学でイベント生成器や断面積計算のための相空間構成を定義するために一般的に使用されます。主な関数には以下が含まれます：

  * `QEDbase.phase_space_dimension`: 出力粒子の数に基づいて相空間の次元を計算します。
  * `QEDbase._build_momenta`: 提供された相空間レイアウトとRAMBOベースのアルゴリズムを使用して出力運動量を構築し、運動量がエネルギーと運動量の保存法則を満たすことを保証します。

# 例

```julia
# 入力とプロセス情報、モデル、および入力座標を定義
psl = FlatPhaseSpaceLayout(input_psl)
build_momenta(process, model, incoming_momenta, psl, out_coords)
```

`FlatPhaseSpaceLayout` は、粒子物理学シミュレーションにおける最終状態相空間を定義するための堅牢なセットアップを提供し、`QEDbase` ルーチンとのモジュラリティと互換性を可能にします。
