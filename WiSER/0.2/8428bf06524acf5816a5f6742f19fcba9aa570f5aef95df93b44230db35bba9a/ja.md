```
rvarlmm(Xs::Array{Matrix}, Zs::Array{Matrix},
Ws::Array{Matrix}, β::Vector, τ::Vector;
respdist = MvNormal, Σγ=[], Σγω=[])
```

`WSVarLmmModel`からのシミュレーションされた応答を生成します：

  * `Xs`: 各クラスタの`X`の配列：平均固定効果の共変量
  * `Zs`: 各クラスタの`Z`の配列：ランダム位置効果の共変量
  * `Ws`: 各クラスタの`W`の配列：被験者内分散の固定効果の共変量
  * `β`: 平均固定効果ベクトル
  * `τ`: 被験者内分散の固定効果ベクトル
  * `respdist`: 応答の分布。デフォルトはMvNormal。
  * `Σγ`: ランダム位置効果の共分散行列。
  * `Σγω`: ランダム位置とランダムスケール効果の共分散行列（完全モデルから生成する場合）

出力は、`Xs, Zs, Ws`の順序に一致するシミュレーションされた応答の配列です。

---

```
rvarlmm!(meanformula::FormulaTerm, reformula::FormulaTerm, 
wsvarformula::FormulaTerm, idvar::Union{Symbol, String},
datatable, β::Vector, τ::Vector; respdist = MvNormal, Σγ=[], Σγω=[],
respname::Symbol = :y)
```

DataFrame `datatable`に基づいてVarLMMモデルからシミュレーションされた応答を生成します。注意：**datatableは、正しい順序で生成するためにグルーピング変数で順序付けられている必要があります。これは`datatable == sort(datatable, idvar)`で確認できます。応答は以下に基づいています：

  * `meanformula`: 平均固定効果`β`のための式を表します（X行列の変数）
  * `reformula`: 平均ランダム効果γのための式を表します（Z行列の変数）
  * `wsvarformula`: 被験者内分散の固定効果τのための式を表します（W行列の変数）
  * `idvar`: グループ化のためのID変数。
  * `datatable`: モデルのためのDataFrame。この関数では**順序が必要**です。
  * `β`: 平均固定効果ベクトル
  * `τ`: 被験者内分散の固定効果ベクトル
  * `respdist`: 応答の分布。デフォルトはMvNormal。
  * `Σγ`: ランダム位置効果の共分散行列。
  * `Σγω`: ランダム位置とランダムスケール効果の共分散行列（完全モデルから生成する場合）
  * `respname`: シミュレーションされた応答変数名を表すシンボル。

`rvarlmm!()`は、データテーブルに新しい応答を表す列を生成します。また、列`y`をベクトルとして返します。生成された応答が一致するためには、データテーブルはID変数で順序付けられている**必要があります**。
