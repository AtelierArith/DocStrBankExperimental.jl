```
ljforcefield = LJForceField(forcefield; r_cutoff=14.0, mixing_rules="Lorentz-Berthelot")
```

Lennard Jonesパラメータを含む.csvファイルを読み込みます（以下の列を含む: `atom,sigma,epsilon`）およびLJForceFieldオブジェクトを構築します。

以下の混合ルールが実装されています：

  * Kong混合ルール: DOI 10.1063/1.1680358
  * Lorentz-Berthelot: https://en.wikipedia.org/wiki/Combining*rules#Lorentz-Berthelot*rules
  * 幾何学的

# 引数

  * `forcefield::String`: フォースフィールドの名前。
  * `r_cutoff::Float64`: ポテンシャルエネルギーをゼロと定義するカットオフ半径（単位: オングストローム）
  * `mixing_rules::String`: フォースフィールドの交差相互作用項を計算するために使用される混合ルール

# 戻り値

  * `ljforcefield::LJForceField`: フォースフィールドパラメータ（純粋なσ、ϵおよび交差相互作用項を含む）を含むデータ構造
