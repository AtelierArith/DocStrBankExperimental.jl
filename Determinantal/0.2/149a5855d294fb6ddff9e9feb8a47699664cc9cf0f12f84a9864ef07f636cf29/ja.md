ProjectionEnsemble(V::Matrix{T},orth=true)

特徴の行列から射影アンサンブルを構築します。ここでは $\mathbf{L} = \mathbf{V}\mathbf{V}^t$ と仮定するので、V は n \times r でなければなりません。ここで n はアイテムの数、r はランクです。V は直交である必要はありません。orth が true（デフォルト）に設定されている場合、QR分解が実行されます。V がすでに直交している場合、この計算はスキップでき、orth を false に設定できます。
