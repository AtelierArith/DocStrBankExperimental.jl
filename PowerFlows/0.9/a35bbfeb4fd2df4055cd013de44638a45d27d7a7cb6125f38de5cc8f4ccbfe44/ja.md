PowerFlowData構造体の定義のための関数。システムデータ、考慮すべき時間期間の数とその名前を指定します。この関数を呼び出しても、電力フローや角度は評価されません。注意：DC電力フロー計算に使用してください。

# 引数:

  * `::DCPowerFlow`:       ABA行列をpower*network*matrixとして、BA行列をaux*network*matrixとして保存するためにDCPowerFlow()を使用します。
  * `sys::PSY.System`:       PowerFlowData構造体で考慮するシステムデータを格納するコンテナ。
  * `time_steps::Int`:       PowerFlowData構造体で考慮する時間期間の数。データを保存するために使用される行列の列数を定義します。デフォルト値 = 1。
  * `timestep_names::Vector{String}`:       引数「time_steps」で定義された時間期間の名前。デフォルト値 = String[]。
  * `check_connectivity::Bool`:       ネットワーク行列の接続性チェックを実行します。デフォルト値 = true。
