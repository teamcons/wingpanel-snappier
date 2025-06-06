mutter_dep = []
libmutter_dep = []

vala_flags = []
c_flags =['-DCLUTTER_ENABLE_COMPOSITOR_API', '-DCLUTTER_ENABLE_EXPERIMENTAL_API',
		'-DCOGL_ENABLE_EXPERIMENTAL_API', '-DCOGL_ENABLE_EXPERIMENTAL_2_0_API']

mutter42_dep = dependency('libmutter-10', version: ['>= 42', '< 43'], required: false)
if mutter42_dep.found()
	libmutter_dep = dependency('libmutter-10', version: '>= 42')
	mutter_dep = [
		libmutter_dep,
		dependency('mutter-cogl-10'), dependency('mutter-cogl-pango-10'),
		dependency('mutter-clutter-10')
	]
	vala_flags = []
endif

mutter43_dep = dependency('libmutter-11', version: ['>= 43', '< 44'], required: false)
if mutter43_dep.found()
	libmutter_dep = dependency('libmutter-11', version: '>= 43')
	mutter_dep = [
		libmutter_dep,
		dependency('mutter-cogl-11'), dependency('mutter-cogl-pango-11'),
		dependency('mutter-clutter-11')
	]
	vala_flags = ['--define', 'HAS_MUTTER43']
endif

mutter44_dep = dependency('libmutter-12', version: ['>= 44', '< 45'], required: false)
if mutter44_dep.found()
	libmutter_dep = dependency('libmutter-12', version: '>= 44')
	mutter_dep = [
		libmutter_dep,
		dependency('mutter-cogl-12'), dependency('mutter-cogl-pango-12'),
		dependency('mutter-clutter-12')
	]
	vala_flags = ['--define', 'HAS_MUTTER43', '--define', 'HAS_MUTTER44']
endif

mutter45_dep = dependency('libmutter-13', version: ['>= 45', '< 46'], required: false)
if mutter45_dep.found()
	libmutter_dep = dependency('libmutter-13', version: '>= 45')
	mutter_dep = [
		libmutter_dep,
		dependency('mutter-mtk-13'), dependency('mutter-cogl-13'),
		dependency('mutter-cogl-pango-13'), dependency('mutter-clutter-13')
	]
	vala_flags = ['--define', 'HAS_MUTTER43', '--define', 'HAS_MUTTER44', '--define', 'HAS_MUTTER45']
endif

mutter46_dep = dependency('libmutter-14', version: ['>= 46', '< 47'], required: false)
if mutter46_dep.found()
	libmutter_dep = dependency('libmutter-14', version: '>= 46')
	mutter_dep = [
		libmutter_dep,
		dependency('mutter-mtk-14'), dependency('mutter-cogl-14'),
		dependency('mutter-cogl-pango-14'), dependency('mutter-clutter-14')
	]
	vala_flags = ['--define', 'HAS_MUTTER43', '--define', 'HAS_MUTTER44', '--define', 'HAS_MUTTER45', '--define', 'HAS_MUTTER46']
endif

mutter47_dep = dependency('libmutter-15', version: ['>= 47', '< 48'], required: false)
if mutter47_dep.found()
	libmutter_dep = dependency('libmutter-15', version: '>= 47')
	mutter_dep = [
		libmutter_dep,
		dependency('mutter-mtk-15'), dependency('mutter-cogl-15'),
		dependency('mutter-cogl-pango-15'), dependency('mutter-clutter-15')
	]
	vala_flags = ['--define', 'HAS_MUTTER43', '--define', 'HAS_MUTTER44', '--define', 'HAS_MUTTER45', '--define', 'HAS_MUTTER46', '--define', 'HAS_MUTTER47']
endif

if mutter_dep.length() == 0
	error ('No supported mutter library found!')
endif

mutter_typelib_dir = libmutter_dep.get_variable('typelibdir')

gala_dep = dependency('gala')
m_dep = meson.get_compiler('c').find_library('m', required: false)

shared_module(
    'wingpanel-interface',
    'Main.vala',
    'DBusServer.vala',
    'BackgroundManager.vala',
    'FocusManager.vala',
    'Utils.vala',
    dependencies: [gala_dep, granite_dep, mutter_dep, m_dep],
    vala_args: vala_flags,
    c_args: c_flags,
    install_rpath: mutter_typelib_dir,
    install: true,
    install_dir: join_paths(get_option('libdir'), 'gala', 'plugins'),
)
