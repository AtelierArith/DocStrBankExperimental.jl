# 参考文献

  * コントローラー（この実装では変更される可能性があります）

[1] G. P. Falconi and F. Holzapfel, “Adaptive Fault Tolerant Control Allocation for a Hexacopter System,” Proc. Am. Control Conf., vol. 2016-July, pp. 6760–6766, 2016.

  * 参照モデル（例：xd, vd, ad, ad*dot, ad*ddot）

[2] S. J. Su, Y. Y. Zhu, H. R. Wang, and C. Yun, “A Method to Construct a Reference Model for Model Reference Adaptive Control,” Adv. Mech. Eng., vol. 11, no. 11, pp. 1–9, 2019.

# 注意

  * （トラッキング制御）コンストラクタの引数 `pos_cmd_func`（時間の関数で、(t) -> position(t) ∈ ℝ^3）を追加してください。

`Dynamics!(env::BacksteppingPositionController)` の内部関数に引数 `pos_cmd` を追加しないでください。

  * （セットポイント制御）コンストラクタの引数 `pos_cmd_func`（時間の関数で、(t) -> position(t) ∈ ℝ^3）を追加しないでください。

`Dynamics!(env::BacksteppingPositionController)` の内部関数に引数 `pos_cmd` を追加してください。
