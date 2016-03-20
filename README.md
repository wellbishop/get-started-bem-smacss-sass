# Get Started with [BEM](http://getbem.com/ "BEM's Homepage") and [SMACSS](https://smacss.com/ "SMACSS's Homepage") with [SASS](http://sass-lang.com/ "SASS's Homepage")

This is just a start point to help you organize the directory structure of your project using
[SMACSS](https://smacss.com/) as the pattern, [SASS](http://sass-lang.com/) as the preprocessor and [BEM](http://getbem.com/) as the methodology. Change it to suit your needs.

## How to

There are two approaches to import the SCSS files:

1. **Index files** *(recommended)*:

    Every subdirectory have an `_index.scss` partial file. Each of this partials is responsible to import the other partials inside that directory.

    ```scss
    @import "base";
    @import "reset";
    ```

    Using this approach you have total control of the order which your files will be imported.

    To use this approach, run the command below:

    ```sh
    $ sass --watch assets/scss:assets/css
    ```

2. **[sass-globbing](https://github.com/chriseppstein/sass-globbing "sass-globbing on Github")**:

    This awesome Ruby gem is powerful to automatically import scss files just pointing the source directory(ies). At the assets path of this approach `(globbing-approach/assets/scss)` we have a scss file called `application.scss`, wich will be used by [sass-globbing](https://github.com/chriseppstein/sass-globbing "sass-globbing on Github") to import the partials.

    ```scss
    @import "base/**/*.scss";
    @import "utilities/**/*.scss";
    @import "layout/**/*.scss";
    @import "themes/default/**/*.scss";
    @import "modules/**/*.scss";
    @import "states/**/*.scss";
    @import "shame/**/*.scss";
    ```

    This approach is awesome, but the awesomeness become a headache when you realize that [sass-globbing](https://github.com/chriseppstein/sass-globbing "sass-globbing on Github") imports the files in alphabetical order. Let's say you have a `_variables.scss` partial, and in the `_header.scss` partial you need some variable defined there. You will get a warning saying that the variable isn't defined. By the way, every project is different. So, if this works for you, go ahead! :)

    To use this approach, be sure to have the gem [sass-globbing](https://github.com/chriseppstein/sass-globbing "sass-globbing on Github") locally installed and then run the command below:

    ```sh
    $ sass -r sass-globbing --watch assets/scss:assets/css
    ```
