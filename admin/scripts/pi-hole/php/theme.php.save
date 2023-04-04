<?php
/* 

*/

// Array of available themes and their description
$available_themes = array();
/* Array key = name used internally, not shown to the user
*  Array[0] = Description
*  Array[1] = Is this a dark mode theme? (Sets background to black during page reloading to avoid white "flashing")
*  Array[2] = Style sheet name
*/
$available_themes['default-light'] = array('Eye-spot default theme (light, default)', false, 'default-light');
$available_themes['default-dark'] = array('Eye-spot midnight theme (dark)', true, 'default-dark');
$available_themes['default-darker'] = array('Eye-spot deep-midnight theme (dark)', true, 'default-darker');
// Option to have the theme go with the device dark mode setting, always set the background to black to avoid flashing
$available_themes['default-auto'] = array('Eye-spot auto theme (light/dark)', true, 'default-auto');
$available_themes['lcars'] = array('Star Trek LCARS theme (dark)', true, 'lcars');

$webtheme = '';
// Try to load theme settings from setupVars.conf
if (isset($setupVars['WEBTHEME'])) {
    $webtheme = $setupVars['WEBTHEME'];
}

// May be overwritten by settings tab
if (isset($_POST['field'])
    && $_POST['field'] === 'webUI'
    && isset($_POST['webtheme'])) {
    $webtheme = $_POST['webtheme'];
}

if (!array_key_exists($webtheme, $available_themes)) {
    // Fallback to default (light) theme is property is not set
    // or requested theme is not among the available
    $webtheme = 'default-auto';
}

$darkmode = $available_themes[$webtheme][1];
$theme = $available_themes[$webtheme][2];

function theme_selection()
{
    global $available_themes, $webtheme;
    foreach ($available_themes as $key => $value) {
        ?><div><input type="radio" name="webtheme" value="<?php echo $key; ?>" id="webtheme_<?php echo $key; ?>" <?php if ($key === $webtheme) { ?>checked<?php } ?>>
        <label for="webtheme_<?php echo $key; ?>"><strong><?php echo $value[0]; ?></strong></label></div>
<?php
    }
}
?>
