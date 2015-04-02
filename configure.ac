AC_PREREQ(2.59)
AC_INIT([gdbus-example], [0.1], [onurmark1@gmail.com])

AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([foreign -Wall -Werror])
AM_PROG_AR

LT_INIT

AC_PROG_CC

AC_CONFIG_FILES(Makefile src/Makefile)

PKG_CHECK_MODULES([GLIB], [glib-2.0 >= 2.40.2])
PKG_CHECK_MODULES([GIO], [gio-unix-2.0 >= 2.40.2])

AC_ARG_WITH([soup],
	[AS_HELP_STRING([--with-soup=PATH/TO/SOUP],[location of the soup library, instead of searching path])],
	[AC_SUBST(SOUP, $with_soup)],
	[AC_PATH_PROGS(SOUP, [soup])])
	
AS_IF([test "x$SOUP" != "x" -a "$SOUP"], [
		AC_MSG_NOTICE([soup found at $SOUP])
	SOUP_LIBS="-L$SOUP/lib -lsoup-2.4"
	AC_SUBST(SOUP_LIBS)
	SOUP_CFLAGS="-I$SOUP/include/libsoup-2.4"
	AC_SUBST(SOUP_CFLAGS)
	],
	AC_MSG_FAILURE(["soup library not found - please use --with-soup=/PATH/TO/SOUP"])
)	

AC_OUTPUT
