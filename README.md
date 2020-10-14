# project to demonstrate Spotless license header bug

## pre-requisites
A Java SE 8 installation available either via the environment variable
`JAVA_HOME` or on the path

## steps

### The `main` branch demonstrates how things worked with Spotless 5.1.0
- Run `git checkout -f main`
- Run `git checkout HEAD~1` followed by `./gradlew spotlessApply`: Run `git
  diff` to see that Spotless has added the copyright header to `HelloWorld.java`
  correctly substituting the current year for `$YEAR`
- Run `git checkout -f main` followed by `./gradlew spotlessApply`: Run `git
  diff` to see that Spotless has fixed the copyright header in `HelloWorld.java`
  making no other changes besides eliminating the extra space before _"All
  Rights Reserved"_

### The `test/5.4.0` branch demonstrates how things continue to work with Spotless 5.4.0
- Run `git checkout -f test/5.4.0`
- Run `git checkout HEAD~1` followed by `./gradlew spotlessApply`: Run `git
  diff` to see that Spotless has added the copyright header to `HelloWorld.java`
  correctly substituting the current year for `$YEAR`
- Run `git checkout -f test/5.4.0` followed by `./gradlew spotlessApply`: Run `git
  diff` to see that Spotless has fixed the copyright header in `HelloWorld.java`
  making no other changes besides eliminating the extra space before _"All
  Rights Reserved"_

### The `test/5.5.0` branch demonstrates how things have changed with Spotless 5.5.0
- Run `git checkout -f test/5.5.0`
- Run `git checkout HEAD~1` followed by `./gradlew spotlessApply`: Run `git
  diff` to see that Spotless has added the copyright header to `HelloWorld.java`
  correctly substituting the current year for `$YEAR` but note that
  `spotlessJava` prints a warning (`Can't parse copyright year '', defaulting to
  2020`)
- Run `git checkout -f test/5.5.0` followed by `./gradlew spotlessApply`: Run `git
  diff` to see that Spotless has fixed the copyright header in `HelloWorld.java`
  but besides eliminating the extra space before _"All Rights Reserved"_ it has
  also changed the year to a range `2020-4464` (it gets the `4464` from the zip
  code in the address in the copyright header)
