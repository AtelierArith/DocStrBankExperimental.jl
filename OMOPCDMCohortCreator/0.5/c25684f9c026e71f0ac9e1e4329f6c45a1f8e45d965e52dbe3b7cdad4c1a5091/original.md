function GetDrugExposureEndDate(drug*exposure*ids; tab = drug_exposure)

Given a list of drug*exposure IDs, find their corresponding drug*exposure*end*date ID.

# Arguments:

  * `drug_exposure_ids` - list of `drug_exposure_id`'s; each ID must be of subtype `Float64`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Drug Exposure table; default `drug_exposure`

# Returns

  * SQL statement comprised of: `:drug_exposure_id` and `:drug_exposure_end_date`
