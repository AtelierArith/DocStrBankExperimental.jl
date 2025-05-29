```
struct OctreeConfig
```

オクツリーを構築するための設定パラメータを格納します

|                 パラメータ |                 型 |                                                         使用法 |                               デフォルト値 |
| ---------------------:| -----------------:| -----------------------------------------------------------:| ------------------------------------:|
|             `NumData` |       `<:Integer` |                                                  データポイントの総数 |                                    - |
|          `MaxTopnode` |       `<:Integer` |                                                    最大トポノード数 |                                10000 |
|         `MaxTreenode` |       `<:Integer` |                                                   最大ツリーノード数 |                               100000 |
|       `TopnodeFactor` |           `Int64` |               Peano-Hilbert曲線が計算領域を分割する際に切り取られるブロックの数を制御します |                                   20 |
|        `ExtentMargin` | `<:AbstractFloat` |                           すべての粒子が領域内にあることを確認するために範囲を少し拡大します |                                1.001 |
|         `PeanoBits2D` |           `Int64` | 各軸で使用されるPeanoビットの長さ。最後のPeanoキーは$2^(2*PeanoBits2D) - 1$になります |                                   31 |
|         `PeanoBits3D` |           `Int64` | 各軸で使用されるPeanoビットの長さ。最後のPeanoキーは$2^(3*PeanoBits3D) - 1$になります |                                   21 |
|             `epsilon` |         `Float64` |                                           ツリーリーフの分離精度を制御します |                               1.0e-4 |
| `ToptreeAllocSection` |       `<:Integer` |                        Toptreeノードが不足している場合、対応する数の空ノードを追加します | $NumDataBase$ * $ToptreeAllocFactor$ |
|    `TreeAllocSection` |       `<:Integer` |                         Octreeノードが不足している場合、対応する数の空ノードを追加します |    $NumDataBase$ * $TreeAllocFactor$ |

ノート:

1. `NumDataBase`はデータポイントの総数の10進数基数です。
2. `ToptreeAllocFactor`と`TreeAllocFactor`を使用して、それぞれ`ToptreeAllocSection`と`TreeAllocSection`を制御します。
