`ShiHeart(; name, τ, LV.V₀, LV.p0, LV.Emin, LV.Emax, LV.τes, LV.τed, LV.Eshift,         RV.V₀, RV.p0, RV.Eₘᵢₙ, RV.Eₘₐₓ, RV.τes, RV.τed, RV.Eshift, LA.V₀, LA_p0,         LA.Emin, LA.Emax, LA.τes, LA.τed, LA.Eshift, RA.V₀, RA.p0, RA.Emin,         RA.Emax, RA.τes, RA.τed, RA.Eshift, AV.CQ, AV.Kp, AV.Kf, AV.Kb, AV.Kv,         AV.θmax, AV.θmin, PV.CQ, PV.Kp, PV.Kf, PV.Kb, PV.Kv, PV.θmax, PV.θmin,         MV.CQ, MV.Kp, MV.Kf, MV.Kb, MV.Kv, MV.θmax, MV.θmin, TV.CQ, TV.Kp, TV.Kf,         TV.Kb, TV.Kv, TV.θmax, TV.θmin)`

Models a whole heart, made up of 2 ventricles (Left & Right Ventricle) and 2 atria (Left & Right atrium) created from the ShiChamber element. Includes the 4 corresponding valves (Aortic, Mitral, Pulmonary and Tricuspid valve) created using the ShiValve element.

Parameters are in the cm, g, s system. Pressure in mmHg. Volume in ml. Flow in cm^3/s (ml/s). Maximum and Minimum angles given in rad, to convert from degrees multiply angle by pi/180.

Named parameters:

`τ`         Length of the cardiac cycle in s

`LV_V₀`     Unstressed left ventricular volume in ml

`LV_p0`     Unstressed left ventricular pressure in mmHg

`LV_Emin`   Minimum left ventricular elastance (diastole) in mmHg/ml

`LV_Emax`   Maximum left ventricular elastance (systole) in mmHg/ml

`LV_τes`    Left ventricular end systolic time in s

`LV_τed`    Left ventricular end distolic time in s

`LV_Eshift` Shift time of contraction - 0 for left ventricle

`RV_V₀`     Unstressed right ventricular volume in ml

`RV_p0`     Unstressed right ventricular pressure in mmHg

`RV_Emin`   Minimum right ventricular elastance (diastole) in mmHg/ml

`RV_Emax`   Maximum right ventricular elastance (systole) in mmHg/ml

`RV_τes`    Right ventricular end systolic time in s

`RV_τed`    Right ventricular end distolic time in s

`RV_Eshift` Shift time of contraction - 0 for right ventricle

`LA_V₀`     Unstressed left atrial volume in ml

`LA_p0`     Unstressed left atrial pressure in mmHg

`LA_Emin`   Minimum left atrial elastance (diastole) in mmHg/ml

`LA_Emax`   Maximum left atrial elastance (systole) in mmHg/ml

`LA_τes`    Left atrial end systolic time in s

`LA_τed`    Left atrial end distolic time in s

`LA_Eshift` Shift time of contraction in s

`RA_V₀`     Unstressed right atrial volume in ml

`RA_p0`     Unstressed right atrial pressure in mmHg

`RA_Emin`   Minimum right atrial elastance (diastole) in mmHg/ml

`RA_Emax`   Maximum right atrial elastance (systole) in mmHg/ml

`RA_τes`    Right atrial end systolic time in s

`RA_τed`    Right atrial end distolic time in s

`RA_Eshift` Shift time of contraction in s

`AV_CQ`     Aortic valve flow coefficent in ml/(s*mmHg^0.5)

`AV_Kp`     Pressure effect on the aortic valve in rad/(s^2*mmHg)

`AV_Kf`     Frictional effect on the aortic valve in 1/s

`AV_Kb`     Fluid velocity effect on the aortic valve in rad/(s*m)

`AV_Kv`     Vortex effect on the aortic valve in rad/(s*m)

`AV_θmax`   Aortic valve maximum opening angle in rad

`AV_θmin`   Aortic valve minimum opening angle in rad

`MV_CQ`     Mitral valve flow coefficent in ml/(s*mmHg^0.5)

`MV_Kp`     Pressure effect on the mitral valve in rad/(s^2*mmHg)

`MV_Kf`     Frictional effect on the mitral valve in 1/s

`MV_Kb`     Fluid velocity effect on the mitral valve in rad/(s*m)

`MV_Kv`     Vortex effect on the mitral valve in rad/(s*m)

`MV_θmax`   Mitral valve maximum opening angle in rad

`MV_θmin`   Mitral valve minimum opening angle in rad

`PV_CQ`     Pulmonary valve flow coefficent in ml/(s*mmHg^0.5)

`PV_Kp`     Pressure effect on the pulmonary valve in rad/(s^2*mmHg)

`PV_Kf`     Frictional effect on the pulmonary valve in 1/s

`PV_Kb`     Fluid velocity effect on the pulmonary valve in rad/(s*m)

`PV_Kv`     Vortex effect on the pulmonary valve in rad/(s*m)

`PV_θmax`   Pulmonary valve maximum opening angle in rad

`PV_θmin`   Pulmonary valve minimum opening angle in rad

`TV_CQ`     Tricuspid valve flow coefficent in ml/(s*mmHg^0.5)

`TV_Kp`     Pressure effect on the tricuspid valve in rad/(s^2*mmHg)

`TV_Kf`     Frictional effect on the tricuspid valve in 1/s

`TV_Kb`     Fluid velocity effect on the tricuspid valve in rad/(s*m)

`TV_Kv`     Vortex effect on the pulmonary valve in rad/(s*m)

`TV_θmax`   Tricuspid valve maximum opening angle in rad

`TV_θmin`   Tricuspid valve minimum opening angle in rad
