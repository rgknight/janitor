NEWS
====

# janitor 0.2.1.9000 (in progress)

## Breaking changes
* The first argument of `adorn_crosstab()` is now "dat" instead of "crosstab" (since the function can be called on any data.frame, not just a result of `crosstab()`)
* The functions `add_totals_row` and `add_totals_col` were combined into a single function, `adorn_totals()`. [(#57)](https://github.com/sfirke/janitor/issues/57).  The `add_totals_` functions are now deprecated and should not be used.

## Features


### Major


### Minor
* `adorn_totals()` and `ns_to_percents()` can now be called on data.frames that have non-numeric columns beyond the first one (they will be ignored) [(#57)](https://github.com/sfirke/janitor/issues/57)
* `adorn_totals("col")` retains factor class in 1st column if that was the input

## Bug fixes
* Long variable names with spaces no longer break `tabyl()` and `crosstab()` [(#87)](https://github.com/sfirke/janitor/issues/87)
* `clean_names()` now handles leading spaces [(#85)](https://github.com/sfirke/janitor/issues/85)
* `adorn_crosstab()` and `ns_to_percents()` work on a 2-column data.frame [(#89)](https://github.com/sfirke/janitor/issues/89)
* `adorn_totals()` now works on a grouped tibble [(#97)](https://github.com/sfirke/janitor/issues/97)

# janitor 0.2.1 (Release date: 2016-10-30)

## Bug fixes
* `tabyl()` and `crosstab()` now appear in the package manual [(#65)](https://github.com/sfirke/janitor/issues/65)
* Fixed minor bug per CRAN request - `tabyl()` and `crosstab()` failed to retain ill-formatted variable names only when using R 3.2.5 for Windows [(#76)](https://github.com/sfirke/janitor/issues/76)
* `add_totals_row()` works on two-column data.frame [(#69)](https://github.com/sfirke/janitor/issues/69)
* `use_first_valid_of()` returns POSIXct-class result when given POSIXct inputs, and handles ba

# janitor 0.2.0 (Release date: 2016-10-03)

## Features

### Major
**Submitted to CRAN!**

### Minor
* The count in `tabyl()` for factor levels that aren't present is now `0` instead of `NA` [(#48)](https://github.com/sfirke/janitor/issues/48)

## Bug fixes
* Can call tabyl() on the result of a tabyl(), e.g., `mtcars %>% tabyl(mpg) %>% tabyl(n)`  [(#54)](https://github.com/sfirke/janitor/issues/54)
* `get_dupes()` now works on variables with spaces in column names [(#62)](https://github.com/sfirke/janitor/issues/62)

## Package management

* Reached 100% unit test code coverage

# janitor 0.1.2

## Features

### Major
* Added a function `adorn_crosstab()` that formats the results of a `crosstab()` for pretty printing.  Shows % and N in the same cell, with the % symbol, user-specified rounding (method and number of digits), and the option to include a totals row and/or column. E.g., `mtcars %>% crosstab(cyl, gear) %>% adorn_crosstab()`.
* `crosstab()` can be called in a `%>%` pipeline, e.g., `mtcars %>% crosstab(cyl, gear)`.  Thanks to [@chrishaid](https://github.com/chrishaid) [(#34)](https://github.com/sfirke/janitor/pull/34)
* `tabyl()` can also be called in a `%>%` pipeline, e.g., `mtcars %>% tabyl(cyl)` [(#35)](https://github.com/sfirke/janitor/issues/35)
* Added `use_first_valid_of()` function [(#32)](https://github.com/sfirke/janitor/issues/32)
* Added minor functions for manipulating numeric data.frames for presentation: `ns_to_percents()`, `add_totals_row()`, `add_totals_col()`,

### Minor

* `crosstab()` returns 0 instead of NA when there are no instances of a variable combination.
* A call like `tabyl(df$vecname)` retains the more-descriptive `$` symbol in the column name of the result - if you want a legal R name in the result, call it as `df %>% tabyl(vecname)`
* Single and double quotation marks are handled by `clean_names()`


## Package management

* Added codecov to measure test coverage
* Added unit test coverage
* Added Travis-CI for continuous integration

# janitor 0.1 (Release date: 2016-04-17)

* Initial draft of skeleton package on GitHub
