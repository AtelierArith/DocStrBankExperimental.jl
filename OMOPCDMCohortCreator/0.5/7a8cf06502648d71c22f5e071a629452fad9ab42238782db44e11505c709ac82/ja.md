function GetDrugExposureStartDate(df:DataFrame, conn; tab = drug_exposure)

:drug*exposure*id列を持つDataFrameを与えると、DataFrame内の指定されたdrug*exposure_idに対応する:drug*exposure*start*dateを持つDataFrameを返します。

`GetDrugExposureStartDate(ids, conn; tab = drug_exposure)`のように、他のすべての引数を受け入れる多重ディスパッチ。
