function GetDrugExposureStartDate(df:DataFrame, conn; tab = drug_exposure)

Given a DataFrame with a :drug*exposure*id column, return the DataFrame with an associated :drug*exposure*start*date corresponding to a given drug*exposure_id in the DataFrame.

Multiple dispatch that accepts all other arguments like in `GetDrugExposureStartDate(ids, conn; tab = drug_exposure)`
