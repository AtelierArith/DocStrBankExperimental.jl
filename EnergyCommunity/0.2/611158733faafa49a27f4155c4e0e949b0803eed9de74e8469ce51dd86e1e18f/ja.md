```
to_least_profitable_coalition_callback(ECModel::AbstractEC, base_group::AbstractGroup=GroupNC(); no_aggregator_group::AbstractGroup=GroupNC())
```

利益分配スキームを入力として受け取り、グランドコアリションに残ることの利益が最も少ないコアリションを返すコールバック関数を返す関数です。返される関数 least*profitable*coalition_callback は、最小利益手続きを計算するために使用されるユーザーごとの利益分配を指定する AbstractDict を引数として受け取ります。

## パラメータ

ECModel : AbstractEC     研究する EC の協力的 EC モデル。     モデルが協力的でない場合、エラーがスローされます。 base*group : AbstractGroup (オプション、デフォルト GroupNC())     利益が計算される基準グループ。 no*aggregator*group : AbstractGroup (オプション、デフォルト GroupNC())     アグリゲーターが利用できない場合のコミュニティの集約グループのタイプ     提供されない場合、同等の非協力モデルが作成され、対応する     ユーザーごとの効用が基準ケースとして使用されます。 number*of*solutions : (オプション、デフォルト 1)     各イテレーションで返されるソリューションの数     number*of*solutions <= 0: すべてのソリューションが返されます     number*of*solutions >= 1: 特定の数のソリューションが返されます relax*combinatorial : (オプション、デフォルト false)     true の場合、完全な最小利益コアリション MILP 問題が連続に緩和されます、     組合せ部分で direct*model : (オプション、デフォルト false)     true の場合、JuMP モデルは直接になります callback*solution : Dict (オプション、デフォルト 空)     最適化の終了ステータスに依存するコールバックの辞書。     キーは JuMP.TerminationStatusCode 型である必要があり、引数として ModelEC を持つ関数を出力します branching*priorities : Bool (オプション、デフォルト true)      分岐優先順位を追加するかどうかを指定するオプション decompose*ANC : Bool (オプション、デフォルト false)     True の場合、no*aggregator*group が ANC であり、メイン最適化モデルが     2 つのモデルに分解されます: (a) アグリゲーターがコアリションにない場合と (b) アグリゲーターがコアリションにある場合     この場合、(a) が最初に最適化され、最適化が指定された閾値を超えると、     実行は (b) を最適化せずに終了します。閾値は、関数によって返されるコールバック関数のオプション入力として提供されます。     それ以外の場合、最適化は (b) で続行されます。 decompose*rel*tolerance : Float     停止基準と現在の結果を比較する decompose*ANC 手続きの相対許容誤差 decompose*abs*tolerance : Float     停止基準と現在の結果を比較する decompose*ANC 手続きの絶対許容誤差

## 返り値

least*profitable*coalition_callback : Function     ユーザーごとの利益分配を表す AbstractDict を入力として受け取る関数
