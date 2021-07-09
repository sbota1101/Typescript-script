# Typescript-script
Checking i18n files:
In order to avoid commit errors concerning the structure and format of the language TS-XML files, the library i18n-integrity-checks.ts checks every base language file and throws specific build time errors whenever the content of the file does not meet the necessary formatting rules, so that, the mistakes can be seen before commit.
The library: checks the duplicate tags of the TS-XML file depending on ID/id and RDID/rdid, if RDID and ID are different, to parse the ts-xml xml2js library was used. checks the structure of the TS-XML file: - the basic syntax according to the specification at w3c  - if start and end tag matches - if namespace prefixes are declared checks if the header is in a valid format or if the values of the header are correctly written checks the indentation of a tag, to be on the same line checks the component of the tag, to have ID, RDID checks the alignment of the tag, if it has comment in front of or behind the tag checks the name of the tags to be correctly written
Parameter	Type	Default	Meaning
appI18nPath	string	'src/assets/i18n'	The path where the tool to look for
languages	string[]	['en', 'en-us', 'en-gb']	The base languages to check for (name of files) - case sensitive
The function can be called, for example from a gulp file, like this:
const { i18nIntegrityCheck } = require('.../duif-devkit');

gulp.task('integrityCheck', function (cb) {
   i18nIntegrityCheck(['src/assets/i18n'], ['en-us']);
   cb();
});
