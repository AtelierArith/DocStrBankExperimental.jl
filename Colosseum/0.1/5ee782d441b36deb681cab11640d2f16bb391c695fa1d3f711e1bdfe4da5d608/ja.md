カメラ歪みパラメータを取得する

引数:     camera*name (str) カメラの名前。後方互換性のため、0,1などのID番号も使用できます。     vehicle*name (str, optional) カメラが関連付けられている車両     external (bool, optional) カメラが外部カメラであるかどうか

戻り値:     List (float) K1, K2, K3, P1, P2にそれぞれ対応する歪みパラメータ値のリスト。
