API制御が確立されている場合はtrueを返します。

falseの場合（これはデフォルトの動作です）、API呼び出しは無視されます。`enableApiControl`への成功した呼び出しの後、`isApiControlEnabled`はtrueを返すべきです。

引数:     vehicle_name (str, optional) 車両の名前

戻り値:     bool: API制御が有効になっているかどうか
