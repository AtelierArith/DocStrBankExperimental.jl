specific*least*core(mode, dist*objective, player*set, utilities, optimizer; verbose)

ゲームの効用関数とプレイヤーセットの大連合によって記述される最小コアの利益分配を計算する関数。この関数は、コラム生成アプローチを使用して、マスタープロブレムに制約を反復的に追加する反復的アプローチを実装しています。そのために、モードカテゴリに保存されたコールバック関数が利用されます。

## 入力

mode : IterMode     コールバック関数への参照を含む計算モード     利益分配スキームが与えられたときに、最悪の利益を持つ連合のセットとその共有される総利益のタプルを返します     callback*worst*coalition は1つの引数（現在の利益分配）を受け取ります dist*objective : Function     最小コアが得られた後の利益分配の目的関数を構築する関数     問題のJuMPモデルとプレイヤーセットの2つの引数を持つ関数であり、     JuMP @NLobjectiveまたは@objectiveコマンドを使用して目的関数を構築します optimizer : Any     計算目的で使用されるJuMPモデルの最適化関数 start*time : (オプション、デフォルトは何も指定しない)     メソッドの初期時間を指定します。何も指定しない場合、値はtime()で初期化されます rtol : Number (オプション、デフォルト 1e-2)     収束プロセスの相対許容誤差 atol : Number (オプション、デフォルト 1e-2)     収束プロセスの絶対許容誤差 lower*bound : Number (オプション、デフォルトは何も指定しない)     問題の変数の下限（利益分配と最悪の連合のマージン） upper*bound : Number (オプション、デフォルトは何も指定しない)     問題の変数の上限（利益分配と最悪の連合のマージン）     何も指定しない場合、値は自動的に大連合の利益に設定されます verbose : Bool (オプション、デフォルト true)     trueの場合、現在の実行状況を示すプログレスバーを表示します raw*outputs : Bool (オプション、デフォルト false)     trueの場合、すべての生の出力を返します use*start*value : Bool (オプション、デフォルト false)     trueの場合、反復プロセスで前の反復値が次の反復の初期化に使用されます max*iter : Bool (オプション、デフォルト 100)     プロセスの最大反復回数 best*objective*stop*option : String (オプション、デフォルトは何も指定しない)     事前設定された値に達したときに下位問題を停止するためのオプションの名前。     このオプションが何も指定されていない場合、この機能は使用されません。     このオプションが指定されている場合、各反復で最小収束基準が追加され、     最小の実行可能な目的関数に達した時点で下位問題を停止します。     この最小目的値は、マスタープロブレムの解に対して、     "best*objective*stop*tolerance"の因子を掛けたものとして得られます。     gurobiが使用されている場合、このオプションはBestObjStopです best*objective*stop*tolerance : Number (オプション、デフォルト 0.05)     "best*objective*stop*option"アプローチで使用される許容誤差 lower*relaxation*stop*option : String (オプション、デフォルトは何も指定しない)     最低限の境界が指定された許容誤差に達したときに最適化の停止基準を設定するために使用されるオプションの名前 tolerance*lower*relaxation*stop : double (オプション、デフォルト 0.0)     lower*relaxation*stop*optionが有効な場合、このオプションはループを停止するために使用される許容誤差を指定します。

## 出力

profit*distribution     プレイヤーによる利益分配 min*surplus     最小余剰を持つ連合の利益の履歴
