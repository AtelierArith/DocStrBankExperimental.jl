GetPatientAgeGroup(     ids;     minuend = :now,     age*groupings = [         [0, 9],         [10, 19],         [20, 29],         [30, 39],         [40, 49],         [50, 59],         [60, 69],         [70, 79],         [80, 89],     ],     tab = person,     ungrouped*label = "Unspecified" )

Return SQL statement that assigns an age group to each patient in a given patient list.  Customized age groupings can be provided as a list.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `age_groupings` - a vector of age groups of the form `[[10, 19], [20, 29],]` denoting an age group of 10 - 19 and 20 - 29 respectively; age values must subtype of `Integer`
  * `minuend` - the year that a patient's `year_of_birth` variable is subtracted from; default `:now`. There are two different options that can be set: 

      * `:now` - the year as of the day the code is executed given in UTC time
      * any year provided by a user as long as it is an `Integer` (such as 2022, 1998, etc.)
  * `tab` - the `SQLTable` representing the Person table; default `person`
  * `ungrouped_label` - the label to assign persons who do not fit to a provided matching age group; default label "Unspecified"

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:age_group`

# Note

Age can be difficult to be calculated consistently. In this case, there are some assumptions made to ensure consistency: 

1. According to the OMOP CDM v5.4, only the variable `year_of_birth` is guaranteed for a given patient. This is one of three options used as the minuend in age calculations.
2. The subtrahend is based on what one chooses for the `minuend` key word argument.

The age is then calculated following what is selected based on 1 and 2. This flexibility is encoded to allow a user to choose how they want age groups calculated as well as clear up an ambiguity on how this is determined.
