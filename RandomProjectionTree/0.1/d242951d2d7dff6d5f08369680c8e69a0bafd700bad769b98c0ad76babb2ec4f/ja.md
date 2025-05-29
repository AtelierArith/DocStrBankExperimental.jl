# function randomProjection(rptree::RPTree)

木を引数の深さまで成長させるドライバーメソッドです。

ノードの分割は並列化されています：

  * $$
    nworkers() > 1
    $$

    の場合、最初のノードは左と右の子に分割され、2つの独立したタスクに @spawnat : any を介して割り当てられます。
  * さらに、もし $Threads.nthreads() > 1$ の場合、次の世代の子は2つの独立したスレッドに分割され、これにより4つの独立したサブツリーが並列に生成されます。

## Returns:

  * 葉のデータベクトルの中心を格納する Array{Vector{Float64},1}。

NOTA : このメソッドは同じ rptree で2回実行することはできません。新しい RPTree を初期化する必要があります。
