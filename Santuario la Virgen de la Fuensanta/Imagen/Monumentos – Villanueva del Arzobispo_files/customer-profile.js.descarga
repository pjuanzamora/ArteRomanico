(function ($) {
    window.booklyCustomerProfile = function (options) {
        $('.bookly-js-show-past', $('.' + options.container)).on('click', function (e) {
            e.preventDefault();
            var $self = $(this),
                $table = $self.prevAll('table.bookly-appointments-table'),
                ladda = Ladda.create(this);
            ladda.start();
            $.get(options.ajaxurl, {
                action: 'bookly_pro_get_past_appointments',
                csrf_token: BooklyCustomerProfileL10n.csrf_token,
                columns: $table.data('columns'),
                custom_fields: $table.data('custom_fields'),
                page: $table.data('page') + 1
            }, function () {
            }, 'json').done(function (resp) {
                ladda.stop();
                if (resp.data.more) {
                    $self.find('span.bookly-label').html(BooklyCustomerProfileL10n.show_more);
                } else {
                    $self.remove();
                }
                if (resp.data.html) {
                    $table.find('tr.bookly--no-appointments').remove();
                    $(resp.data.html).hide().appendTo($table).show('slow');
                    $table.data('page', $table.data('page') + 1);
                }
            });
        });
    };
})(jQuery);