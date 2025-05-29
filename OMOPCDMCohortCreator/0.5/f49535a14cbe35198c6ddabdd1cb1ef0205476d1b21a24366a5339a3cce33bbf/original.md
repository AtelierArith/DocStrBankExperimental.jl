GetDrugExposureIDs(ids, conn; tab = drug_exposure)

Given a list of person IDs, find their drug exposure.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the the drug*exposure table; default `drug*exposure`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:drug_exposure_id`
