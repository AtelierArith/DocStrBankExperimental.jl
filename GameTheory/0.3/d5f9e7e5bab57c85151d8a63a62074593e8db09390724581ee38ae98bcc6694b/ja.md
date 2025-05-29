```
best_response([rng=GLOBAL_RNG], player, opponents_actions;
              tie_breaking=:smallest, tol=1e-8)
```

`opponents_actions`に対する最適応答アクションを返します。

# 引数

  * `rng::AbstractRNG=GLOBAL_RNG` : 擬似乱数生成器; `tie_breaking=:random` の場合にのみ関連します。
  * `player::Player` : プレイヤーインスタンス。
  * `opponents_actions::Union{Action,ActionProfile,Nothing}` : N-1人の対戦相手のアクションのプロファイル。N=2の場合、実数のベクトル（この場合、対戦相手の混合アクションとして扱われます）または整数のスカラー（この場合、対戦相手の純粋なアクションとして扱われます）でなければなりません。N>2の場合、N-1の整数（純粋なアクション）またはN-1の実数のベクトル（混合アクション）のタプルでなければなりません。（特異なケースN=1の場合、`nothing`でなければなりません。）
  * `tie_breaking::Symbol` : タイをどのように解決するかを制御します（詳細はReturnsを参照）。
  * `tol::Real` : 最適応答アクションを決定するために使用される許容誤差。

# 戻り値

  * `::Int` : `tie_breaking=:smallest` の場合、最小のインデックスを持つ最適応答アクションを返します; `tie_breaking=:random` の場合、最適応答アクションからランダムに選ばれたアクションを返します。
