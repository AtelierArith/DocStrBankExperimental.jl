```julia
shock_detector(Se, deg)
shock_detector(Se, deg, S0)
shock_detector(Se, deg, S0, κ)

```

強い不連続性に解が属するかどうかを検出します

*P. O. Persson と J. Peraire. 不連続ガレルキン法のためのサブセル衝撃捕捉. 第44回AIAA航空宇宙科学会議および展示会, 2006年。*

  * @arg Se = log10(<(u - û)²>/<u²>), u は直交多項式に基づく解で、û は1つ下の切り捨て次数の同じ解
  * @arg deg: 多項式の自由度
  * @arg S0: Se の基準点
  * @arg κ: 鋭く滑らかな衝撃プロファイルを得るために十分大きく選択する必要がある経験的パラメータ
