T,V = lanczosTridiag(A,b,k;tol,doReorth)

ランチョス法による因子分解の取得

A = Vk Tk Vk'

ここで、Aは実対称のn×n行列、Tkはk×kの三重対角行列であり、n×k行列Vkの列は直交しています。

実装は以下の通りです：

Paige, C. C. (1972).  固有値問題のためのランチョス法の計算的変種。IMA Journal of Applied Mathematics.

必要な入力：

A       - A*xを計算する関数、例：x -> A*x   b       - 右辺ベクトル   k       - クリロフ部分空間の次元

オプションの入力：

tol      - 停止許容誤差   doReorth - (デフォルト=false) 完全な再直交化を行うためにtrueに設定

出力：

Tk    - 疎三重対角行列  Vk    - 基底ベクトル
