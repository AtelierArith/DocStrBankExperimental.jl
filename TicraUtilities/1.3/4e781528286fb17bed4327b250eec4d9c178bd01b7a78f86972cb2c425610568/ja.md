```
teps2p(tep::TEPscatter, d, freq; name="tep_periodic", class="created_by_teps2p")
```

散乱TEPオブジェクト（タイプ`TEPscatter`）を周期的ユニットセルTEPオブジェクト（タイプ`TEPperiodic`）に変換します。

`d`は前面と背面の参照平面間の距離であり、`Unitful`量です。`freq`は周波数であり、こちらも`Unitful`量です。`tep`と`freq`は両方ともスカラーまたは同じ長さのベクトルである必要があります。後者の場合、各エントリは特定の周波数に対応します。

## 使用例

```
using Unitful: @u_str
freqs = [1.2u"GHz", 2u"GHz"] # tepsが2つのTEPscatterオブジェクトのベクトルであると仮定
d = 2.3u"mm"
tep_periodic = teps2p(teps, d, freqs)
```

# 拡張ヘルプ

入力引数`freq`は必須です。なぜなら、周波数は`TEPperiodic`オブジェクトに保存されているデータの一部ですが、`TEPscatter`オブジェクトには含まれていないからです。さらに、`freq`と`d`の両方の引数が必要です。なぜなら、`TEPperiodic`はユニットセルの実際の前面と背面の表面に位置する位相参照平面を使用するのに対し、`TEPscatter`は前面の表面のみを前面および背面の入射の位相参照平面として使用するからです。したがって、これらの引数は背面表面の入射反射および前面と背面の表面の入射透過のために必要な位相補正を計算するために必要です。この位相補正は、一部の係数に必要な符号の変更に加えて行われます。
