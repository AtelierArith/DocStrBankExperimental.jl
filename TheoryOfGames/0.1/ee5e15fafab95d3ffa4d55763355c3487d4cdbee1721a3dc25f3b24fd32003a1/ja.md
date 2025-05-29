least*core(mode, player*set, utilities, optimizer; verbose)

ゲームの効用関数とプレイヤーセットのグランドコアリションによって記述される最小コアの利益分配を計算する関数。この関数は、マスタープロブレムに制約を反復的に追加するためにカラム生成アプローチを使用する反復的アプローチを実装しています。そのために、モードカテゴリに保存されたコールバック関数が利用されます。

## 入力

mode : IterMode     利益分配スキームを与えたときに、最悪の利益を持つコアリションのセットとその共有される総利益のタプルを返すコールバック関数への参照を含む計算モード     callback*worst*coalitionは1つの引数（現在の利益分配）を受け取ります optimizer : Any     計算目的のために使用されるJuMPモデルの最適化関数 start*time : (オプション、デフォルトはnothing)     メソッドの初期時間を指定します。何も指定しない場合、値はtime()で初期化されます rtol : Number (オプション、デフォルトは1e-2)     収束プロセスの相対許容誤差 atol : Number (オプション、デフォルトは1e-2)     収束プロセスの絶対許容誤差 lower*bound : Number (オプション、デフォルトはnothing)     問題の変数の下限（利益分配と最悪のコアリションのマージン） upper*bound : Number (オプション、デフォルトはnothing)     問題の変数の上限（利益分配と最悪のコアリションのマージン）     何も指定しない場合、値は自動的にグランドコアリションの利益に設定されます verbose : Bool (オプション、デフォルトはtrue)     trueの場合、現在の実行状況を示すプログレスバーが表示されます raw*outputs : Bool (オプション、デフォルトはfalse)     trueの場合、すべての生の出力が返されます use*start*value : Bool (オプション、デフォルトはfalse)     trueの場合、反復プロセスで前の反復値が次の反復の初期化に使用されます max*iter : Bool (オプション、デフォルトは100)     プロセスの最大反復回数 preload*coalitions : Vector (オプション、デフォルトは空)     反復手続きが始まる前に自動的に含めるべきコアリションのリスト best*objective*stop*option : String (オプション、デフォルトはnothing)     事前に設定された値に達したときに下位問題を停止するためのオプションの名前。     このオプションがnothingの場合、この機能は使用されません。     このオプションがnon-nothingの場合、各反復で、最小限の収束基準が追加され、     最小限の実行可能な目的関数に達したときに下位問題を停止します。     この最小目的値は、マスタープロブレムの解に対して得られ、     "best*objective*stop*tolerance"の因子で乗算されます。     gurobiが使用されている場合、このオプションはBestObjStopです best*objective*stop*tolerance : Number (オプション、デフォルトは0.05)     "best*objective*stop*option"アプローチで使用される許容誤差 lower*relaxation*stop*option : String (オプション、デフォルトはnothing)     最低限の境界がtolerance*lower*relaxation*stopオプションで指定された許容誤差に達したときに、最適化の停止基準を設定するために使用されるオプションの名前 tolerance*lower*relaxation*stop : double (オプション、デフォルトは0.0)     lower*relaxation*stop*optionが有効な場合、このオプションはループを停止するために使用される許容誤差を指定します。

## 出力

profit*distribution     プレイヤーによる利益分配 min*surplus     最小余剰を持つコアリションの利益履歴
