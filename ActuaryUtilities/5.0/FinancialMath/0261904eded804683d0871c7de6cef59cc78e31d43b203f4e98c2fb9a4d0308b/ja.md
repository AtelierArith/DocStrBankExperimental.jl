```
duration(Macaulay(),interest_rate,cfs,times)
duration(Modified(),interest_rate,cfs,times)
duration(DV01(),interest_rate,cfs,times)
duration(interest_rate,cfs,times)             # 修正デュレーション
duration(interest_rate,valuation_function)    # 修正デュレーション

```

マコーレー、修正、またはDV01デュレーションを計算します。 `times`は省略可能で、評価は最初の期間の終わりから始まる均等に間隔を置いたキャッシュフローを仮定します。

計算されたデュレーションは、`interest_rate`の周期性の慣習に依存することに注意してください：`Periodic`利回り（またはその慣習を持つ利回りモデル）は、周期性に応じて異なる現在価値から導かれる`Continous`よりもわずかに異なる計算されたデュレーションになります。

`Modified()`または`Macaulay()`を引数として与えない場合、デフォルトで`Modified()`になります。

  * 修正デュレーション：利回り変化のポイントごとの相対的変化。
  * マコーレー：キャッシュフロー加重平均時間。
  * DV01：ベーシスポイント（百分の一パーセントポイント）ごとの絶対的変化。

# 例

キャッシュフローと時間のベクトルを使用

```julia-repl
julia> times = 1:5;

julia> cfs = [0,0,0,0,100];

julia> duration(0.03,cfs,times)
4.854368932038835

julia> duration(Periodic(0.03,1),cfs,times)
4.854368932038835

julia> duration(Continuous(0.03),cfs,times)
5.0

julia> duration(Macaulay(),0.03,cfs,times)
5.0

julia> duration(Modified(),0.03,cfs,times)
4.854368932038835

julia> convexity(0.03,cfs,times)
28.277877274012614

```

任意の値関数を使用：

```julia-repl
julia> lump_sum_value(amount,years,i) = amount / (1 + i ) ^ years
julia> my_lump_sum_value(i) = lump_sum_value(100,5,i)
julia> duration(0.03,my_lump_sum_value)
4.854368932038835
julia> convexity(0.03,my_lump_sum_value)
28.277877274012617

```
