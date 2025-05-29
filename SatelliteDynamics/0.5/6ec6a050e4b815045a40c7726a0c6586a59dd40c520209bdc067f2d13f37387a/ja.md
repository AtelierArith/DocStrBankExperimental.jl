/––––––––––––––––––––––––––––––––––––––-

  * 
  * ```
                            procedure sgp4
    ```
  * 
  * この手続きは、宇宙司令部のsgp4予測モデルです。これは、元々
  * spacetrack report #3で別々に発表されたsgp4とsdp4の
  * 更新された統合版です。このバージョンは、コードの歴史と
  * 開発を説明するaiaaの論文（2006）からの方法論に従っています。
  * 
  * 著者        : デビッド・ヴァラド                  719-573-2600   2005年6月28日
  * 
  * 入力        :
  * tle	 - sgp4init()呼び出しからの初期化された構造体。
  * tsince	 - エポックからの時間（分）
  * 
  * 出力       :
  * r           - 位置ベクトル                     km
  * v           - 速度                            km/sec
  * 戻りコード - エラー時は非ゼロ。
  * ```
                  1 - 平均要素、ecc >= 1.0またはecc < -0.001またはa < 0.95 er
    ```
  * ```
                  2 - 平均運動が0.0未満
    ```
  * ```
                  3 - 擾乱要素、ecc < 0.0またはecc > 1.0
    ```
  * ```
                  4 - 半長軸 < 0.0
    ```
  * ```
                  5 - エポック要素がサブ軌道
    ```
  * ```
                  6 - 衛星が減衰した
    ```
  * 
  * ローカル変数        :
  * am          -
  * axnl, aynl        -
  * betal       -
  * cosim   , sinim   , cosomm  , sinomm  , cnod    , snod    , cos2u   ,
  * sin2u   , coseo1  , sineo1  , cosi    , sini    , cosip   , sinip   ,
  * cosisq  , cossu   , sinsu   , cosu    , sinu
  * delm        -
  * delomg      -
  * dndt        -
  * eccm        -
  * emsq        -
  * ecose       -
  * el2         -
  * eo1         -
  * eccp        -
  * esine       -
  * argpm       -
  * argpp       -
  * omgadf      -
  * pl          -
  * r           -
  * rtemsq      -
  * rdotl       -
  * rl          -
  * rvdot       -
  * rvdotl      -
  * su          -
  * t2  , t3   , t4    , tc
  * tem5, temp , temp1 , temp2  , tempa  , tempe  , templ
  * u   , ux   , uy    , uz     , vx     , vy     , vz
  * inclm       - 傾斜
  * mm          - 平均異常
  * nm          - 平均運動
  * nodem       - 昇交点の赤経
  * xinc        -
  * xincp       -
  * xl          -
  * xlm         -
  * mp          -
  * xmdf        -
  * xmx         -
  * xmy         -
  * nodedf      -
  * xnode       -
  * nodep       -
  * np          -
  * 
  * 結合      :
  * getgravconst-
  * dpper
  * dpspace
  * 
  * 参考文献    :
  * hoots, roehrich, norad spacetrack report #3 1980
  * hoots, norad spacetrack report #6 1986
  * hoots, schumacher and glover 2004
  * vallado, crawford, hujsak, kelso  2006  ––––––––––––––––––––––––––––––––––––––*/
