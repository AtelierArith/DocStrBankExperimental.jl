Create a dictionary of poverty measures.

This is based on the [World Bank's Poverty Handbook](http://documents.worldbank.org/curated/en/488081468157174849/Handbook-on-poverty-and-inequality) by  Haughton and Khandker.

Arguments:

  * `rawdata` - an nxm array of real nunbers; each row is an observation; one col should be a weight, another is income;  positions assumed to be 1 and 2 unless weight and incomepos are supplied
  * `line` - a poverty line, assumed same for all obs (so income is assumed to be already equivalised)
  * `foster_greer_thorndyke_alphas` - coefficients for FGT poverty measures; note that FGT(0)  corresponds to headcount and FGT(1) to gap; count and gap are computed directly anyway  but it's worth checking one against the other.
  * `growth` is (e.g.) 0.01 for 1% per period, and is used for 'time to exit' measure.

Output is  dictionary with an entry for each measure.

The measures are:

  * `headcount`;
  * `gap`;
  * `Foster Greer Thorndyke`, for each of the values in `foster_greer_thorndyke_alphas`;
  * `Watts`;
  * `time to exit`, for the supplied growth rate;
  * `Shorrocks`;
  * `Sen`.

See World Bank, ch. 4.
