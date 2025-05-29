```
function plot_bandstr(h::tb_crys; kpath, names = missing, proj_types=missing, proj_orbs = missing, proj_nums=missing)
```

`tb_crys`オブジェクトのバンド構造をプロットします。`proj_types`、`proj_orbs`、`proj_nums`のいずれかを指定することで、投影されたバンド構造を実行することもできます。

k-pathはkpath配列とnamesによって指定されます。

プロットする前にscf計算を行う必要があります。

# 引数

  * `h::tb_crys` - バンドをプロットしたいタイトバインディングオブジェクト。必須の引数です。
  * `kpath=[0.5 0 0 ; 0 0 0; 0.5 0.5 0.5; 0 0.5 0.5; 0 0 0 ;0 0 0.5]` - `nk` × 3配列のk点パス（高対称点）。
  * `npts=30,` - 高対称k点間のポイント数。
  * `names=missing` - `nk`文字列配列。高対称k点の名前。
  * `proj_types=missing` - 投影するタイプ。`proj_types="H"`または`proj_types=["H", "O"]`が有効です。
  * `proj_orbs=missing` - 投影する軌道。`proj_orbs=:s`または`proj_orbs=[:s, :p]`のいずれか。
  * `proj_nums=missing` - 投影する原子番号。`proj_nums=1`または`proj_nums=[1, 2]`のいずれか。
  * `efermi=missing` - フェルミエネルギーを指定できます。デフォルトは`h`から取得します。
  * `color="blue"` - 線の色を指定します。
  * `MarkerSize=missing"` - マーカーサイズを指定します。
  * `yrange=missing"` - y範囲を指定します。例：`yrange=[-0.7, 0.3]`
  * `plot_hk=false` - 通常のバンド構造以外のものをプロットします。`H`または`S`の固有値や成分をプロットするために`:Seig, :Heig, :Hreal, :Himag, :Sreal, :Simag`のいずれかを指定できます。主にデバッグ用です。
  * `align="vbm"` - デフォルトまたは`"valence"`は、価電子帯の最大値をゼロエネルギーに揃えます。`"min"`は最小固有値に揃え、`"fermi"`または`"ef"`はフェルミレベルに揃えます。
  * `clear_pervious=true` - 新しいものを追加する前にプロットをクリアします。
  * `do_display=true` - プロットを表示します。`false`の場合、表示なしのノードで使用できます。`Plots`の`savefig`を使用して保存された画像を生成することはできます。

```
