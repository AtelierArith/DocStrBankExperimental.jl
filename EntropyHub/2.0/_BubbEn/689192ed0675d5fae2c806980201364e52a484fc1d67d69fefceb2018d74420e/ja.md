```
Bubb, H = BubbEn(Sig)
```

データシーケンス（`Sig`）から次元 m = 2 のバブルエントロピー（`Bubb`）と条件付きレーニーエントロピー（`H`）の推定値をデフォルトのパラメータを使用して返します：埋め込み次元 = 2、時間遅延 = 1、対数 = 自然対数

```
Bubb, H = BubbEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Logx::Real=exp(1))
```

指定された「キーワード」引数を使用してデータシーケンス（`Sig`）のバブルエントロピー（`Bubb`）の推定値を返します：

# 引数：

`m`     - 埋め込み次元、1より大きい整数   

```
      BubbEnは各次元 [2,...,m] の推定値を返します
```

`tau`   - 時間遅延、正の整数    

`Logx`  - 対数の底、正のスカラー 

# 参照： `PhasEn`, `MSEn`

# 参考文献：

```
[1] George Manis, M.D. Aktaruzzaman and Roberto Sassi,
    "Bubble entropy: An entropy almost free of parameters."
    IEEE Transactions on Biomedical Engineering
    64.11 (2017): 2711-2718.
```
