`ShiHeart(; name, τ, LV.V₀, LV.p0, LV.Emin, LV.Emax, LV.τes, LV.τed, LV.Eshift,         RV.V₀, RV.p0, RV.Eₘᵢₙ, RV.Eₘₐₓ, RV.τes, RV.τed, RV.Eshift, LA.V₀, LA_p0,         LA.Emin, LA.Emax, LA.τes, LA.τed, LA.Eshift, RA.V₀, RA.p0, RA.Emin,         RA.Emax, RA.τes, RA.τed, RA.Eshift, AV.CQ, AV.Kp, AV.Kf, AV.Kb, AV.Kv,         AV.θmax, AV.θmin, PV.CQ, PV.Kp, PV.Kf, PV.Kb, PV.Kv, PV.θmax, PV.θmin,         MV.CQ, MV.Kp, MV.Kf, MV.Kb, MV.Kv, MV.θmax, MV.θmin, TV.CQ, TV.Kp, TV.Kf,         TV.Kb, TV.Kv, TV.θmax, TV.θmin)`

心臓全体をモデル化し、2つの心室（左心室と右心室）と2つの心房（左心房と右心房）をShiChamber要素から作成します。対応する4つの弁（大動脈弁、僧帽弁、肺動脈弁、三尖弁）をShiValve要素を使用して作成します。

パラメータはcm、g、sシステムで表されます。圧力はmmHgで、体積はmlで、流量はcm^3/s（ml/s）で表されます。最大および最小角度はラジアンで与えられ、度からラジアンに変換するには角度にπ/180を掛けます。

名前付きパラメータ：

`τ`         心拍周期の長さ（秒）

`LV_V₀`     ストレスのない左心室の体積（ml）

`LV_p0`     ストレスのない左心室の圧力（mmHg）

`LV_Emin`   最小左心室弾性（拡張期）（mmHg/ml）

`LV_Emax`   最大左心室弾性（収縮期）（mmHg/ml）

`LV_τes`    左心室の収縮期末時間（秒）

`LV_τed`    左心室の拡張期末時間（秒）

`LV_Eshift` 収縮のシフト時間 - 左心室の場合は0

`RV_V₀`     ストレスのない右心室の体積（ml）

`RV_p0`     ストレスのない右心室の圧力（mmHg）

`RV_Emin`   最小右心室弾性（拡張期）（mmHg/ml）

`RV_Emax`   最大右心室弾性（収縮期）（mmHg/ml）

`RV_τes`    右心室の収縮期末時間（秒）

`RV_τed`    右心室の拡張期末時間（秒）

`RV_Eshift` 収縮のシフト時間 - 右心室の場合は0

`LA_V₀`     ストレスのない左心房の体積（ml）

`LA_p0`     ストレスのない左心房の圧力（mmHg）

`LA_Emin`   最小左心房弾性（拡張期）（mmHg/ml）

`LA_Emax`   最大左心房弾性（収縮期）（mmHg/ml）

`LA_τes`    左心房の収縮期末時間（秒）

`LA_τed`    左心房の拡張期末時間（秒）

`LA_Eshift` 収縮のシフト時間（秒）

`RA_V₀`     ストレスのない右心房の体積（ml）

`RA_p0`     ストレスのない右心房の圧力（mmHg）

`RA_Emin`   最小右心房弾性（拡張期）（mmHg/ml）

`RA_Emax`   最大右心房弾性（収縮期）（mmHg/ml）

`RA_τes`    右心房の収縮期末時間（秒）

`RA_τed`    右心房の拡張期末時間（秒）

`RA_Eshift` 収縮のシフト時間（秒）

`AV_CQ`     大動脈弁の流量係数（ml/(s*mmHg^0.5)）

`AV_Kp`     大動脈弁に対する圧力効果（rad/(s^2*mmHg)）

`AV_Kf`     大動脈弁に対する摩擦効果（1/s）

`AV_Kb`     大動脈弁に対する流体速度効果（rad/(s*m)）

`AV_Kv`     大動脈弁に対する渦効果（rad/(s*m)）

`AV_θmax`   大動脈弁の最大開口角（rad）

`AV_θmin`   大動脈弁の最小開口角（rad）

`MV_CQ`     僧帽弁の流量係数（ml/(s*mmHg^0.5)）

`MV_Kp`     僧帽弁に対する圧力効果（rad/(s^2*mmHg)）

`MV_Kf`     僧帽弁に対する摩擦効果（1/s）

`MV_Kb`     僧帽弁に対する流体速度効果（rad/(s*m)）

`MV_Kv`     僧帽弁に対する渦効果（rad/(s*m)）

`MV_θmax`   僧帽弁の最大開口角（rad）

`MV_θmin`   僧帽弁の最小開口角（rad）

`PV_CQ`     肺動脈弁の流量係数（ml/(s*mmHg^0.5)）

`PV_Kp`     肺動脈弁に対する圧力効果（rad/(s^2*mmHg)）

`PV_Kf`     肺動脈弁に対する摩擦効果（1/s）

`PV_Kb`     肺動脈弁に対する流体速度効果（rad/(s*m)）

`PV_Kv`     肺動脈弁に対する渦効果（rad/(s*m)）

`PV_θmax`   肺動脈弁の最大開口角（rad）

`PV_θmin`   肺動脈弁の最小開口角（rad）

`TV_CQ`     三尖弁の流量係数（ml/(s*mmHg^0.5)）

`TV_Kp`     三尖弁に対する圧力効果（rad/(s^2*mmHg)）

`TV_Kf`     三尖弁に対する摩擦効果（1/s）

`TV_Kb`     三尖弁に対する流体速度効果（rad/(s*m)）

`TV_Kv`     三尖弁に対する渦効果（rad/(s*m)）

`TV_θmax`   三尖弁の最大開口角（rad）

`TV_θmin`   三尖弁の最小開口角（rad）
