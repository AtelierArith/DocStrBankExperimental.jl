```
apes(echogram, model, solver[; params, result_handler, safe_precision, distributed])
```

逆モデル`model`と解法`solver`によって定義された自動確率エコーソルバーを、`echogram`の音響バックスキャッターデータに対して実行します。

# 引数

  * `echogram::DimArray`: 線形領域における音響バックスキャッターデータ（すなわち、体積バックスキャッタ係数$s_v$、面積バックスキャッタ係数$s_a$、または海上面積散乱係数$NASC$）。`DimArray`の最後の次元は`:F`という名前で、音響周波数をインデックス付けする必要があります。他のすべての次元は空間/時間座標を参照する必要があります。
  * `model::Function`: Turing.jlまたはDynamicPPL.jlで定義された確率的逆モデル。このモデルは`model(data, params)`というシグネチャを持つ必要があり、`data`と`params`には音響データと追加のパラメータが含まれます。詳細については以下を参照してください。
  * `solver::AbstractSolver`: `model`で指定された逆問題を解くために使用される方法。詳細については`MCMCSolver`および`MAPSolver`を参照してください。
  * `params`: `model`に渡すオプションの追加パラメータ。
  * `result_handler`: ソルバーの出力を変換するためのオプションの関数（例えば、マルコフ連鎖の平均を計算することによって）。
  * `distributed::Bool=false`: echogramセルにモデルをフィットさせる際に、利用可能なすべてのプロセッサを使用するかどうか。

# 詳細

この関数は、Turing.jlを使用して定義された確率的逆バックスキャッターモデルを、複数周波数のエコーグラム内の各スペクトルに適用します。モデルのコンストラクタは、2つの引数を受け入れる必要があります：

  * `data`: ドット表記でアクセス可能な`NamedTuple`または他の構造体で、`coords`、`freqs`、および`backscatter`というフィールドを持ちます。これらは観測された音響データを含みます。モデルはすべてを使用する必要はありません。
  * `params`: モデルによって使用される定数や補助情報を含むオプションの`NamedTuple`または他のオブジェクト。
