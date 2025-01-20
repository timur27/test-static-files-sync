<meta content="2025-01-20 11:48:22" name="post_date_gmt">
<meta content="Add currencies and symbols" name="post_title">
<meta content="0" name="menu_order">
<!-- wp:paragraph -->
<p>Add this code to your child theme's <code>functions.php</code> file or via a plugin that allows custom functions to be added, such as the <a href="https://wordpress.org/plugins/code-snippets/">Code Snippets</a> plugin. Avoid adding custom code directly to your parent theme's functions.php file, as this will be wiped entirely when you update the theme.</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>if ( ! function_exists( 'YOUR_PREFIX_add_currency_name' ) ) {<br>  /**<br>   * Add custom currency<br>   * <br>   * @param array $currencies Existing currencies.<br>   * @return array $currencies Updated currencies.<br>   */<br>  function YOUR_PREFIX_add_currency_name( $currencies ) {<br>    $currencies&#91;'ABC'] = __( 'Currency name', 'YOUR-TEXTDOMAIN' );<br><br>    return $currencies;<br>  }<br>  add_filter( 'woocommerce_currencies', 'YOUR_PREFIX_add_currency_name' );<br>}<br><br>if ( ! function_exists( 'YOUR_PREFIX_add_currency_symbol' ) ) {<br>  /**<br>   * Add custom currency symbol<br>   * <br>   * @param string $currency_symbol Existing currency symbols.<br>   * @param string $currency Currency code.<br>   * @return string $currency_symbol Updated currency symbol(s).<br>   */<br>  function YOUR_PREFIX_add_currency_symbol( $currency_symbol, $currency ) {<br>    switch( $currency ) {<br>      case 'ABC': $currency_symbol = '$'; break;<br>    }<br><br>    return $currency_symbol;<br>  }<br>  add_filter('woocommerce_currency_symbol', 'YOUR_PREFIX_add_currency_symbol', 10, 2);<br>}<br></code></pre>
<!-- /wp:code -->